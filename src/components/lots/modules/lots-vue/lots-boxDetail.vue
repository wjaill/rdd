<template>
    <div class="lots-boxdetail">
         <router-view></router-view>
        <div class="head-height">
            <lots-box-detail-head></lots-box-detail-head>
       </div>
       <div class="lots-articaldetail">
            <div class="lots-articaldetailtop">
                <h1>{{data.essay_title}}</h1>
                <h2>
                    <span class="spanone">
                        <i>
                            <b class="fa fa-commenting-o"></b>
                            <strong>13</strong>
                        </i>
                        <i class="itwo">
                            <b class="fa fa-eye"></b>
                            <strong>{{data.essay_views_num}}</strong>
                        </i>
                    </span>
                    <span class="spantwo">
                        <b>{{data.essay_time}}</b>
                        
                    </span>
                </h2>
            </div>
            <p></p>
            <div class="lots-articaldetailcenter">
                
                <span v-for=" (im,i) in data.essay_image" :key="i"><img :src="im"></span>
                <div class="font">
                    {{data.essay}}
                </div>
            </div>
       </div>
    </div>
</template>

<script>
import LotsBoxDetailHead from './lots-boxdetailhead'
import axios from "axios"
export default {
    name:"lots-boxdetail",
    components:{
        LotsBoxDetailHead
    },
    data(){
        return{
            data:'',
            img:[],
            essay_id:'',
        }
    },
    mounted(){
        axios.post("/api/v1/found/essay_detail",{essay_id:this.$route.query.essay_id}).then((res)=>{
            this.data = res.data.data[0]
            this.img = this.data.essay_image
            //this.essay_id = this.data.essay_id
            console.log(this.data)
        })
    }
}
</script>

<style lang="scss" scoped>
.lots-boxdetail{
    width:100%;
    height:100%;
    position: fixed;
    top:0;
    z-index:1000;
    background:#fff;
    .head-height{
        width:100%;
        height:44px;
    }
}
</style>

