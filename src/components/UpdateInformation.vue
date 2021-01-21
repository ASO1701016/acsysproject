<template>
    <div id="#app">
        <div class="jumbotron jumbotron-fluid bg-dark ">
            <div class="container">
                <h1 class="display-4 font-weight-lighter" style="font-family: Helvetica,'Yu Gothic UI',serif">更新情報</h1>
            </div>
        </div>
        <div class="container">
            <div class="row">
                <div class="col-3 lead">
                    日付
                </div>
                <div class="col lead ">
                    内容
                </div>
            </div><!-- /.row -->
            <hr>
            <div class="row mb-4">
                <div class="col-3 lead">
                    11月27日
                </div>
                <div class="col lead">
                    Topページを少し更新しました。
                    <div class="mb-2">
                        以下の機能を公開しました。<br>
                        ・Twitter投稿<br>
                        ・パスワードの変更<br>
                    </div>
                    以下のバグを修正しました。<br>
                    ・新規登録の誕生日に存在しない日付でも登録できるのを修正しました。。<br>
                    ・カロリー入力のカレンダー表示を修正しました。
                </div>
            </div><!-- /.row mb-4 -->
            <div class="row mb-4">
                <div class="col-3 lead">
                    11月17日
                </div>
                <div class="col lead">
                    Twitterカードが表示されるようになりました！<br>
                </div>
            </div><!-- /.row mb-4 -->
            <div class="row mb-4">
                <div class="col-3 lead">
                    11月4日
                </div>
                <div class="col lead">
                    サーバーのログが取れていない問題を解決しました。<br>
                </div>
            </div><!-- /.row mb-4 -->
            <div class="row mb-4">
                <div class="col-3 lead">
                    10月31日
                </div>
                <div class="col lead">
                    Topページの反応速度を向上しました。<br>
                </div>
            </div><!-- /.row mb-4 -->
            <div class="row mb-4">
                <div class="col-3 lead">
                    10月19日
                </div>
                <div class="col lead">
                    Topページと更新情報ページの下部に、Twitterシェアボタンと作成者、連絡先を記載しました。<br>
                </div>
            </div><!-- /.row mb-4 -->
            <div class="row mb-4">
                <div class="col-3 lead">
                    10月10日
                </div>
                <div class="col lead">
                    タイトルをわかりやすく変更しました。<br>
                </div>
            </div><!-- /.row mb-4 -->
            <div class="row mb-4">
                <div class="col-3 lead">
                    9月29日
                </div>
                <div class="col lead">
                    Topページのデザインを変更しました。<br>
                    更新情報を追加しました。<br>
                    <span class="text-danger mt-3">使えなくなる機能があります！！</span><br>
                    現在カロリーでの選択入力を使えなくしています。もっと使いやすくなるように改善しますのでもうしばらくお待ちください。
                </div>
            </div><!-- /.row mb-4 -->
            <div class="row mb-4">
                <div class="col-3 lead">
                    9月17日
                </div>
                <div class="col lead">
                    Twiiterアカウントを開設しました。新しく出来た機能や更新情報を呟いていきたいと思います。
                    ぜひフォローしてください！
                    <a href="https://twitter.com/acsys_calorie">Twitterアカウントはこちら</a>
                </div>
            </div><!-- /.row mb-4 -->
            <div class="row mb-4">
                <div class="col-3 lead">
                    8月20日
                </div>
                <div class="col lead">
                    <div class="mb-2">
                        以下の機能を公開しました。<br>
                        ・カレンダー<br>
                        ・統計<br>
                        ・トレーニング<br>
                        ・登録情報の変更<br>
                    </div>
                    以下のバグを修正しました。<br>
                    ・新しく摂取カロリーを登録すると、前に登録した摂取カロリーが消えること。<br>
                    ・統計機能でリストにある貯金の表示ミスを修正しました。
                </div>
            </div><!-- /.row mb-4 -->
            <div class="row mb-4">
                <div class="col-3 lead">
                    8月14日
                </div>
                <div class="col lead">
                    サイト公開しました。
                </div>
            </div><!-- /.row mb-4 -->
        </div><!-- /.container -->
        <hr class="featurette-divider  mt-5">
        <footer class="container">
            <div class="text-center">
                <div class="sosyal">
                    <a href="https://twitter.com/acsys_calorie" class="twitter">acsys公式Twitter</a>
                </div>
            </div>
            <p class="float-right"><button class="btn btn-outline-success" @click="scrollTop()">トップに戻る</button></p>
            <p>2020 麻生ビジネス専門学校情報工学科2班<br>
                お問い合わせ:1701017@st.asojuku.ac.jp</p>
        </footer><!-- /.footer -->
    </div>
</template>

<script>
    export default {
        name: "UpdateInformation",
        methods:{
            scrollTop: function(){
                window.scrollTo({
                    top: 0,
                    behavior: "instant"
                })
            },
        }
    }
</script>

<style scoped>
    .jumbotron {
        background-position: center 60%;
        color: white;
    }
    .sosyal {
        margin: 50px auto;
    }
    .twitter {
        background-color: #008DDE;
        box-shadow: 0 4px 0 #0078BD;

        display: inline;
        position: relative;
        font-family: Arial;
        font-size: 14px;
        font-weight: bold;
        text-align: center;
        text-decoration: none;
        color: white;
        border-radius: 5px;
        padding: 14px 80px;
    }
    .twitter:active {
        top: 2px;
        box-shadow: 0 2px 0 #0078BD;
    }
    .twitter:hover {
        background-color: #1397D8;
    }
</style>
