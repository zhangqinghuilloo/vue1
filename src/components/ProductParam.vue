<template>
    <div class="nav-bar">
        <div class="nb-t"></div>
        <div class="nb-b">
            <div class="nbt-left">{{title}}</div>
            <div class="nbt-right">
                <ul>
                    <li><a href="#">概述</a><span>|</span></li>
                    <li><a href="#">参数</a><span>|</span></li>
                    <li><a href="#">用户评价</a></li>
                    <li class="ll"><a href="#" class="llgm" v-on:click="buy">立即购买</a></li>
                </ul>
            </div>
        </div>
        <div class="nb-t"></div>
    </div>
</template>
<script>
    export default{
        name:'nav-bar',
        props:{
            title:String
        },
        methods:{
            buy(){
                let id=this.$route.params.id;
                this.$router.push(`/detail/${id}`)
            }
        }
    }
</script>
<style lang="scss">
    .nav-bar{
        background: #FFFFFF;
    }
    .nb-t{
        border: 1px solid #E5E5E5;
    }
    .nb-b{
        height: 80px;
        line-height: 80px;
        background: #FFFFFF;
    }
    .nbt-left{
        float: left;
        height: 80px;
        line-height: 80px;
        font-size: 18px;
        color: #333333;
        margin-left: 210px;
        font-weight: bolder;
    }
    .nbt-right{
        float: right;
        margin-right: 0px;
    }
   
    .nbt-right ul li{
        display: inline-block;
       
    }
    .nbt-right ul li a{
        width: 20px;
        font-size: 14px;
        color: #666666;
    }
    .nbt-right ul li span{
        display: inline-block;
        margin-left: 10px;
        margin-right: 10px;
    }
    .ll{
        margin-left: 11px;
        width: 100px;
        background: #FF7301;
        height: 30px;
        line-height: 30px;
    }
    .nbt-right ul li .llgm{
        width: 110px;
        height: 30px;
        color: #FFFFFF;
        font-size: 12px;
        
    }
</style>