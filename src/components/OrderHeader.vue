<template>
    <div class="order-header">
        <div class="oh-logo"></div>
        <div class="oh-title">{{title}}</div>
        <div class="oh-text"><slot name="tip"></slot></div>
        <div class="clear"></div>
    </div>
</template>
<script>
    export default{
        name:'order-header',
        props:{
            title:String
        }
    }
</script>
<style lang="scss">
    .order-header{
        height: 112px;
        
    }
    .oh-logo{
        width: 53px;
        height: 52px;
        background: url(/imgs/logo-mi.png) no-repeat center;
        background-size: contain;
        margin-top: 29px;
        float: left;
    }
    .oh-title{
        margin-left: 54px;
        float: left;
        color: #333333;
        font-size: 28px;
        margin-top: 29px;
    }
    .oh-text{
        margin-top: 25px;
        float: left;
        color: #999999;
        font-size: 14px;
        text-align: center;
        height: 52px;
        line-height: 52px;
        margin-left: 170px;
    }
    .clear{
        clear: both;
    }
</style>