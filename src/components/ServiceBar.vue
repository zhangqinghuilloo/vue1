<template>
    <div class="service">
        <div class="sb">
            <ul>
                <li class="yy"><img src="/imgs/icon-setting.png" class="tu"><span>预约维修服务</span></li>
                <li class="yy"><img src="/imgs/icon-7day.png" class="tu"><span>7天无理由退货</span></li>
                <li class="yy"><img src="/imgs/icon-15day.png" class="tu"><span>15天免费换货</span></li>
                <li class="man yy"><img src="/imgs/icon-post.png" class="tu"><span>满150元包邮</span></li>
            </ul>
        </div>
    </div>
</template>
<script>
    export default{
        name:'service-bar'
    }
</script>
<style lang="scss">
    .service{
        margin-top: 50px;
        padding-top: 33px 0;
        text-align: center;
        background: #FFFFFF;
        height: 80px;
    }
    ul{
        text-align: center;

    }
    .yy{
        display: inline-block;
        width: 20%;
        font-size: 16px;
        color: #666666;
        height: 80px;
        line-height: 80px;
        position: relative;
        
    }
    .yy:after{
        content: '';
        width: 1px;
        height: 34px;
        border:1px solid #E5E5E5;
        margin-left:90px ;
    }
    .man:after{
        display: none;
    }
    .tu{
        width: 20px;
        height: 20px;
        margin-right: 4px;
        
        
    }
    .tu img{
        width: 20px;
        height: 20px;
        
        
    }
</style>