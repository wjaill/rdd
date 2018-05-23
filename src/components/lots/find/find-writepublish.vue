<template>
    <div class="find-writepublish">
       <div class="find-writehead">
            <router-link :to="'/find-fo'"  tag="b" class="fa fa-chevron-left"> </router-link>
            <span>发帖</span>
            <b @click="publish">发布</b>
       </div>
        <find-write-box :message="message"></find-write-box>
    </div>
</template>

<script>
import axios from 'axios'
import { Toast } from 'mint-ui';
import FindWriteBox from './find-writebox.vue'
    export default {
        name:"find-writepublish",
        components:{
           FindWriteBox
        },
        data(){
            return{
                message:{
                    code:'',
                    kind:'',
                    title:'',
                    essay:'',
                    user_id:'',
                    images:[] 
                } 
            }
        },
        methods:{
            publish(){
                 let that = this;
                 if(this.message.kind == ''|| this.message.title == '' || this.message.essay == ''){
                      Toast({
                             message: '请完善信息',
                        });
                        return;
                 }
                 let url = '/api/v1/found/writepublish'
        		 let params = {
                    kind:that.message.kind,
                    title:that.message.title,
                    essay:that.message.essay,
                    image:that.message.images,
                    user_id: JSON.parse(localStorage.getItem("user_info")).LoginOnData.uid //这是用户id，是需要挂载在vuex上面的
                  }
        		axios.post(url,params).then(res=>{
        			that.code=res.data
                    console.log(res)
                    if(that.code.code == 200){
                        Toast({
                             message: '发表成功',
                        });
                    }
        		})
                setTimeout(function(){
                     that.$router.push('/find-fo')
                },2000)
               
            }
        }
    }        
</script>

<style lang="scss" scoped>

</style>