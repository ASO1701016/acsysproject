<template>
  <!-- PoseNetモデルの読み込み -->
  <div id="app" class="container">
    <h1>デモ</h1>
    <p id='status'></p>
    <div class="container">
      <div class="dash-unit">

        <h2 class="a-spacing-none">回数</h2>
        <div class="count">
          <div id="disp_count">{{ count_value }}</div>
        </div>

        <h3>選択トレーニング</h3>
        <div id="training">
        </div>

        <div class="reset">
          <button id="btn_reset" @click="reset();">リセット</button>
          <div class="judge">
            <button id="btn_comment" class="btn btn-outline-success" @click="comment();">終了</button>
          </div>
        </div>
        <canvas ref="canvas" id="canvas" width="500" height="500"></canvas>
        <video ref="video" id="video" width="500" height="500" autoplay></video>
      </div>
    </div>
  </div>

</template>

<script>
export default {
  // props:{
  //   EventLink:{
  //     type:String,
  //   }
  // }
}
</script>
<script src="https://cdn.jsdelivr.net/npm/@tensorflow-models/posenet"></script>

<script>
import p5 from 'p5'
import ml5 from 'ml5'
// import Training from '@/components/Training';

export default {

  data: function () {
    const post_data = {
      judge_ID: '',
      burned_ID: '',
      judge_rate: '',
      count_disp: document.getElementById("dips_count"),
    }
    return {
      video: {},
      posenet: '',
      poses: [],
      count_value: 0,
      should_count: true,
      count_disp: document.getElementById("dips_count"),
      reset_btn: document.getElementById("btn_reset"),
      comment_btn: document.getElementById("btn_comment"),
      keypoint: '',
      canvas: {},
    }
  },

  mounted() {
    //Webカメラ
    this.video = this.$refs.video
    if (navigator.mediaDevices && navigator.mediaDevices.getUserMedia) {
      navigator.mediaDevices.getUserMedia({ video: true }).then(stream => {
        this.video.srcObject = stream
        this.video.play()
      })
    }

    //poseNetのセットアップ処理
    // this.video = p5.createCapture();
    this.posenet = ml5.poseNet(this.video,this.modelReady());
    let val=[];
    const ref = this;
    this.posenet.on('pose', function (results) {
      val = this.poses = results;
      ref.draw(val)
    })
  },
  methods: {
    selectCategory(value){
      },
    //canvasにVIDEOの内容を描画
    capture () {
      this.canvas = this.$refs.canvas
      this.canvas.getContext('2d').drawImage(this.video, 0, 0, 500, 500)
    },

    //poseNetのモデルが読み取られたか確認するメソッド
    modelReady: function () {
      console.log('モデルの読取に成功しました')
    },

    //回数をカウントするメソッド
    count: function () {
      this.count_value += 1;
      this.count_disp.innerHTML = this.count_value;
    },

    draw: function (poses) {
      this.poses = poses;
      if (this.poses.length > 0) {
        let pose = this.poses[0].pose;
        this.keypoint = pose.keypoints[0];
        for (let i = 0; i < this.poses.length; i++) {
          // poseが持つ情報を出力
          let pose = this.poses[i].pose
          //本当は0.6以上だが挙動確認のため低い値に設定
          if (pose.score >= 0.3) {
            //ユーザーが判定ラインより下にいった時
            //本当は250以上だが挙動確認のため低い値に設定
            if (pose.nose.y >= 220.0 && this.should_count) {
              this.count_value += 1;
              this.should_count = false;
            } else if (pose.nose.y <= 240.0) {
              // 姿勢が元に戻った判定
              this.should_count = true;
            }
            if (this.count_value === 10) {
              document.getElementById('disp_count').style.color = "#FF0000";
            }
          }
        }
        this.drawKeypoints();
      }
      else {
        console.log('pose情報が見当たりません')
      }
    },



    drawKeypoints: function () {
      for (let i = 0; i < this.poses.length; i++) {
        let pose = this.poses[i].pose;
        for (let j = 0; j < pose.length; j++) {
          this.keypoint = pose.keypoints[j];
          if (this.keypoint > 0.2) {
            // シェイプの塗りに使用するカラーを設定
            this.keypoint.fill(color(0, 0, 255));
            // 線とシェイプの枠線の描画に使用するカラーを設定
            this.keypoint.stroke(20);
            this.keypoint.ellipse(this.keypoint.position.x, this.keypoint.position.y, 10, 10);
          }
        }
      }
    },

    //回数の値をリセットするメソッド
    reset: function () {
      console.log("リセットしました")
      this.count_value = 0;
    },
    comment: function(){
      alert('今回の回数は'+this.count_value+'でした')
    },
  }
}

</script>
