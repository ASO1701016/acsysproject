<template>
    <div class="container">
        <!-- 姿勢判定機能リンク -->
        <div class="row">
            <label class="col-lg-3 col-auto col-form-label" >身体活動レベル</label>
            <select v-bind:key="form.id" name=”TrainingDetail” v-model="form.training_detail"  class="form-control col-sm-7 text-left">
                <option value=1 selected="selected" >スクワット</option>
                <option value=2>腕立て伏せ</option>
                <option value=3>腹筋</option>
            </select>

            <div class="row mt-3 mb-5">
                <button id="send_btn" class="btn btn-success" @click="new SendData(form.id)">決定</button>
            </div>

            <!--            <button id="droplist_button" class="btn btn-success col-8 mx-auto" @click="dropList"></button>-->

            <div class="text-center mt-3" >
                <!--              <button id="post_btn" class="btn btn-success col-8 mx-auto"  name="SetMenu" @click="NextPage">開始</button>-->
                <!--              <router-link :to="{ name: 'formjudge', params: { met: 'met'}}" >開始</router-link >-->
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "CountTraining",
        data(){
            return{
                selectedCategory:'',
                categories:[
                    {id:1,name:'スクワット'},
                    {id:2,name:'腕立て伏せ'},
                    {id:3,name:'腹筋'},
                ],
                form: {
                    training_detail: '',
                },
            }
        },
        methods:{
            SendData(EventId){
                let EventLink = {name:'formjudge',EventLink:EventId}
                this.$router.push(EventLink).catch(() => {})
            },
        },
    }
</script>

<style scoped>

</style>