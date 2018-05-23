<template>
    <div class="lots-boxdetailhead">
        <b @click="toin" class="yo-ico">&#xe605;</b>
        <span>文章详情</span>
        <b @click="topj">评价</b>
        <!-- <b>评价</b> -->
    </div>
</template>

<script>
export default {
    name:"lots-boxdetailhead",
    methods:{
        topj(){
            this.$router.push({path:'/lotindex/lotBoxDetail/lotPingjia',query:{essay_id:this.$route.query.essay_id}});
        },
        toin(){
            this.$router.push({path:'/lotindex',query:{essay_id:this.$route.query.essay_id}});
        }
    }
}

</script>

<style lang="scss" scoped>
  
</style>

