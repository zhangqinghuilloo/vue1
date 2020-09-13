<template>
    <div class="footer">
        <div class="hang"></div>
        <div class="footer_logo">
            <img src="/imgs/logo-footer.png" alt="小米">
            <p>小米商城</p>
        </div>
        <div class="footer_top">
            <a>张庆辉的商城</a><span>&nbsp;|&nbsp;</span>
            <a>张庆辉的商城</a><span>&nbsp;|&nbsp;</span>
            <a>张庆辉的商城</a><span>&nbsp;|&nbsp;</span>
            <a>张庆辉的商城</a><span>&nbsp;|&nbsp;</span>
            <a>张庆辉的商城</a>
            <p>Copyright&copy;2020 <a href="http://www.baidu.com">www.baidu.com</a>All Rights Reserved</p>
        </div>
        
    </div>
</template>
<script>
    export default{
        name:'nav-footer'
    }
</script>
<style lang="scss">
    .hang{
        height: 4px;
        background: #FF6600;
    }
    .footer{
        height: 233px;
        background: #343434;
        text-align: center;
    }
    .footer_logo{
        color: #999999;
        margin-top: 46px;
    }
    .footer_logo img{
        width: 53px;
        height: 36px;
    }
    .footer_logo p{
        margin-top: 13px;
        font-size: 16px;
    }
    .footer_top{
        margin-top: 31px;
    }
    .footer_top a{
        color: #999999;
        font-size: 16px;
    }
    .footer_top span{
        color: #999999;
        
    }
    .footer_top p{
        color: #999999;
        font-size: 16px;
    }
    .footer_top p a{
        color: blue;
        display: inline-block;
    }
</style>