<template>
    <div class="header">
        <div class="header_top">
            <div class="header_top_left">
                <a href="#" class="a1">松果出行</a>
                <a href="#" class="a1">MIUI</a>
                <a href="#" class="a1">云服务</a>
                <a href="#" class="a1">协议规则</a>
            </div>
            <div class="header_top_right">
            <a href="#" class="a2" v-if="username">{{username}}</a>
            <a href="#" class="a2" v-if="!username" v-on:click="login">登录</a>
            <a href="#" class="a2" v-if="username">我的订单</a>
            <a href="#" class="a3" v-on:click="goToCart"><span class="cart"></span>购物车{{cartCount}}</a>
            </div>
        </div>
        <div class="header_Bottom">
            <div class="header_Bottom_logo">
                <a href="#"></a>
            </div>
            <div class="header_Bottom_left">
                <div class="hBl_nav">
                    <span>小米手机</span>
                    <div class="children">
                        <ul>
                            <li class="product" v-for="(item,index) in phoneList" :key="index">
                                <a v-bind:href="'/#/product/'+item.id" target="_blank">
                                    <div class="pro_img">
                                        <img :src="item.mainImage">
                                    </div>
                                    <div class="pro_name">{{item.name}}</div>
                                    <div class="pro_price">{{item.price}}</div>
                                </a>
                            </li>
                            
                        </ul>
                    </div>
                </div>
                <div class="hBl_nav">
                    <span>Redmi红米</span>
                    <div class="children"></div>
                </div>
                <div class="hBl_nav">
                    <span>电视</span>
                    <div class="children">

                    </div>
                </div>
            </div>
            <div class="header_Bottom_right">
                <div class="wapper">
                    <input type="text" name="sousuo">
                    <a href="#"></a>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
    export default{
        name:'nav-header',
        data(){
            return{
                username:this.$store.state.username,
                phoneList:[]
            }
        },
        computed:{
            uesrname(){
                return this.$store.state.username;
            },
                cartCount(){
                    return this.$store.state.cartCount;
                }
        },
        mounted(){
            this.getProductList();
        },
        methods:{
            login(){
                this.$router.push('/login');
            },
            getProductList(){
                this.axios.get('/products',{
                params:{
                    categoryId:'100012',
                    pageSize:6
                }
            }).then((res)=>{
                    this.phoneList=res.list;
            })
            },
            goToCart(){
                this.$router.push('/cart');
            }
        }
    }
</script>
<style lang="scss">
    .header{
        
        height:151px;
        background:#343434;
        margin-left:auto;
        margin-right:auto;
    }
    .header_top{ 
        height:39px;
        line-height:39px;
        overflow: hidden;
    }
    .header_top_left{
        float: left;
        margin-left: 210px;
        font-size: 12px;
    }
    .header_top_right{
        float: right;
        margin-right: 170px;
    }
    .a1{
        display: inline-block;
        margin-right: 17px;
        color:#B0B0B0;
    }
    .a2{
        display: inline-block;
        margin-left: 19px;
        color:#B0B0B0;
        font-size: 12px;
    }
    .a3{
        display: inline-block;
        color:white;
        font-size: 12px;
        margin-left: 18px;
        background:#FF6600 ;
        width: 110px;
        text-align: center;
    }
    .cart{
        width: 16px;
        height: 12px;
        margin-right: 4px;
        background: url('/imgs/icon-cart-checked.png') no-repeat center;
        background-size: contain;
        display: inline-block;
    }
    .header_Bottom{
        height: 112px;
        line-height: 112px;
        background: white;
        position: relative;
    }
    .header_Bottom_logo{
        width: 55px;
        height: 55px;
        background: #FF6600;
        float: left;
        line-height: 55px;
        position: absolute;
        left: 0;
        top: 29px;
    }
    .header_Bottom_logo a{
        display: inline-block;
        width: 110px;
        height: 55px;
    }
    .header_Bottom_logo a:before{
        content: '';
        display: inline-block;
        width: 55px;
        height: 55px;
        background: url('/imgs/mi-logo.png') no-repeat center;
        background-size: contain;
        transition-duration: 0.3s;
    }
    .header_Bottom_logo a:after{
        content: '';
        display: inline-block;
        width: 55px;
        height: 55px;
        background: url('/imgs/mi-home.png') no-repeat center;
        background-size: contain;
    }
    .header_Bottom_logo a:hover:before{
        margin-left: -55px;
        transition-duration: 0.3s;
    }
    .header_Bottom_left{
        margin-left: 209px;
        float: left;
        width: 240px;
        height: 112px;
        line-height: 112px;

    }
    .hBl_nav{
        display: inline-block;
        font-weight: bolder;
        font-size: 16px;
        color: #333333;
        margin-right: 20px;
    }
    .hBl_nav span{
        cursor: pointer;
    }
    .hBl_nav:hover{
        color:#FF6600;

    }
    .hBl_nav:hover .children{
        height: 220px;
        opacity: 1;
    }
    .hBl_nav .children{
        height: 0px;
        opacity: 0;
        position: absolute;
        top: 122px;
        left: 0;
        width: 1226px;
        border-top:1px solid #E5E5E5;
        box-shadow: 0px 7px 6px 0px rgba(0,0,0,0.11);
        z-index:10; 
        background-color: #ffffff;
        overflow:hidden;
    }
    .hBl_nav .children .product{
        width: 16.6%;
        height: 220px;
        float: left;
        position: relative;
    }
    .hBl_nav .children .product .pro_img{
        height: 100px;
        position: absolute;
        top: 30px;
        left: 60px;
    }
    .hBl_nav .children .product .pro_name{
        position: absolute;
        height: 40px;
        top: 100px;
        left: 70px;
        color:#333333;
    }
    .hBl_nav .children .product .pro_price{
        position: absolute;
        height: 40px;
        top: 120px;
        left: 70px;
        color:#FF6600;
      
    }
    .hBl_nav .children .product:before{
        content: '';
        position: absolute;
        top: 28px;
        right: 0;
        border-left: 1px solid #D7D7D7;
        height: 100px;
        width: 1px;
    }
    .hBl_nav .children .product:last-child:before{
        display: none;
    }
    .header_Bottom_right{
        float:right;
        height: 50px;
        position: absolute;
        right: 0;
        top: 31px;
    }
    .wapper{
        border: 1px solid #E0E0E0;
        width: 318px;
        height: 50px;
        position: relative;
    }
    .header_Bottom_right input{
        width: 247px;
        height: 50px;
        padding-left: 14px;
        float: left;
        border: none;
        border-right: 1px solid #E0E0E0;

    }
    .header_Bottom_right a{
        display: inline-block;
        width: 18px;
        height: 18px;
        background: url('/imgs/icon-search.png') no-repeat center ;
        background-size: contain;
        position: absolute;
        top: 16px;
        right: 19px;
    }
</style>