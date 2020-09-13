<template>
    <div class="index">
        <div class="swiper-box">
            <div class="nav">
                <ul class="nav-u">
                    <li class="nav-u-i">
                        <a href="#">手机 电话卡</a>
                        <div class="children">
                            <ul v-for="(item,i) in menuList" v-bind:key="i">
                                <li v-for="(sub,s) in item" v-bind:key="s">
                                    <a v-bind:href="sub?'/#/product/'+sub.id:''">
                                        <img v-bind:src="sub?sub.img:'/imgs/item-box-3.jpg'">
                                        {{sub?sub.name:'Redmi K20 Pro'}}
                                    </a>
                                </li>
                            </ul>
                        </div>
                    </li>
                    <li class="nav-u-i">
                        <a href="#">电视 盒子</a>
                    </li>
                    <li class="nav-u-i">
                        <a href="#">笔记本 平板</a>
                    </li>
                    <li class="nav-u-i">
                        <a href="#">家电 插线板</a>
                    </li>
                    <li class="nav-u-i">
                        <a href="#">出行 穿戴</a>
                    </li>
                    <li class="nav-u-i">
                        <a href="#">耳机 音箱</a>
                    </li>
                    <li class="nav-u-i">
                        <a href="#">电源 配件</a>
                    </li>
                    <li class="nav-u-i">
                        <a href="#">生活 箱包</a>
                    </li>
                </ul>
            </div>
            <swiper v-bind:options="swiperOption">
                <swiper-slide v-for="(item,index) in slideList" v-bind:key="index">
                    <a v-bind:href="'/#/product/'+item.id"><img v-bind:src="item.img"></a>
                </swiper-slide>
                <div class="swiper-pagination" slot="pagination"></div>
                <div class="swiper-button-prev" slot="button-prev"></div>
                <div class="swiper-button-next" slot="button-next"></div>
            </swiper>
        </div>
        <div class="ads-box">
            <a v-bind:href="'/#/product/'+item.id" v-for="(item,index) in adsList" v-bind:key="index">
                <img v-lazy="item.img">
            </a>
        </div>
        <div class="banner">
            <a v-bind:href="'/#/product/30'"><img v-lazy="'/imgs/banner-1.png'"></a>
        </div>
        <div class="product-box">
            <h2 class="sj">手机</h2>
            <div class="product-b">
                <div class="prob-left">
                    <a href="/#/product/35"><img v-lazy="'/imgs/mix-alpha.jpg'"></a>
                </div>
                <div class="prob-right">
                    <div class="prob-right-t">
                        <ul>
                            <li v-for="(item,index) in productList" v-bind:key=index>
                                <div class="a">
                                    <span>新品</span>
                                    <a href="/#/product/35"><img v-lazy="'/imgs/nav-img/nav-4.png'"></a>
                                    <p class="itn">小米9 6GB+128GB</p>
                                    <p class="its">骁龙855，索尼4800万超广角微距</p>
                                    <p class="itp">2999</p>
                                </div>
                            </li>
                        </ul>
                    </div>
                    <div class="prob-right-b">
                        <ul>
                            <li v-for="(item,index) in productList" v-bind:key=index>
                                <div class="a">
                                    <span>新品</span>
                                    <a href="#"><img v-lazy="'/imgs/nav-img/nav-4.png'"></a>
                                    <p class="itn">小米9 6GB+128GB</p>
                                    <p class="its">骁龙855，索尼4800万超广角微距</p>
                                    <p class="itp">2999</p>
                                </div>
                            </li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
        <ServiceBar></ServiceBar>
    </div>
</template>
<script>
    import ServiceBar from './../components/ServiceBar'
    import { Swiper, SwiperSlide, directive} from 'vue-awesome-swiper'
    import 'swiper/css/swiper.css'
    export default{
        name:'index',
        components:{
            Swiper,
            SwiperSlide,
            ServiceBar
        },
        directive:{
            swiper:directive
        },
        data(){
            return{
                swiperOption:{
                    autoplay:true,
                    loop:true,
                    effect : 'cube',
                    cubeEffect: {
                        slideShadows: true,
                        shadow: true,
                        shadowOffset: 100,
                        shadowScale: 0.6
                    },
                    pagination: {
                        el: '.swiper-pagination',
                        clickable:true
                    },
                    navigation: {
                        nextEl: '.swiper-button-next',
                        prevEl: '.swiper-button-prev',
                    },
                },
                slideList:[{
                    id:'42',
                    img:'/imgs/slider/slide-1.jpg'
                },{
                    id:'45',
                    img:'/imgs/slider/slide-2.jpg'
                },{
                    id:'46',
                    img:'/imgs/slider/slide-3.jpg'
                },{
                    id:'',
                    img:'/imgs/slider/slide-4.jpg'
                },{
                    id:'',
                    img:'/imgs/slider/slide-5.jpg'
                }],
                menuList:[
                    [{
                        id:30,
                        img:'/imgs/item-box-1.png',
                        name:'小米CC9'
                    },{
                        id:31,
                        img:'/imgs/item-box-2.png',
                        name:'小米8青春版'
                    },{
                        id:32,
                        img:'/imgs/item-box-3.jpg',
                        name:'Redmi K20 Pro'
                    },{
                        id:33,
                        img:'/imgs/item-box-4.jpg',
                        name:'移动4G专区'
                    }],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0]
                ],
                adsList:[
                    {
                        id:33,
                        img:'/imgs/ads/ads-1.png'
                    },{
                        id:48,
                        img:'/imgs/ads/ads-2.jpg'
                    },{
                        id:45,
                        img:'/imgs/ads/ads-3.png'
                    },{
                        id:47,
                        img:'/imgs/ads/ads-4.jpg'
                    }
                ],
                productList:[
                    {id:1},{id:2},{id:3},{id:4}
                ]
            }
        },
        
    }
</script>
<style lang="scss">
    .index .swiper-box .swiper-container{
        height: 451px;
    }
    .index .swiper-box .swiper-container img{
        height: 100%;
        width: 100%;
    }
    .ads-box{
        margin-top: 14px;
        margin-bottom: 31px;
    }
    .nav{
        position: absolute;
        width: 264px;
        height: 451px;
        z-index: 10;
        background: #55585a7a;
        
    }
    .nav-u{
        margin-top:26px;
    }
    .nav a{
        display: block;
        color: #FFFFFF;
    }
    .nav-u-i{
        font-size: 16px;
        height: 50px;
        line-height: 50px;
        text-align: left;
        width: 234px;
        color: #FFFFFF;
        padding-left: 30px;  
    }
    .nav-u-i:hover{
        background:#FF6600;
        
    }
    .nav-u-i:hover .children{
        display: block;
    }
    .children{
        width: 962px;
        height: 451px;
        background: white;
        position: absolute;
        top: 0;
        left: 264px;
        display: none;
    }
    .children ul{
        height: 75px;

    }
    .children ul a{
        font-size: 14px;
        color: black;
    }
    .children ul li{
        height: 75px;
        width: 225px;
        line-height: 75px;
        display: inline-block;
    }
    .children ul li a img{
        width: 42px;
        height: 40px;
    }
    .swiper-button-prev{
        left:274px
    }
    .ads-box a{
        display: inline-block;
        width: 296px;
        height: 167px;
        margin-right: 14px;
    }
    .ads-box a img{
        width: 296px;
        height: 167px;
    }
    .ads-box a:last-child{
        margin-right: 0;
    }
    .banner{
        width: 1226px;
        height: 130px;
        margin-bottom: 50px;
    }
    .banner img{
        width: 1226px;
        height: 130px;
    }
    .product-box{
        height: 740px;
        background: #F5F5F5;
    }
    .sj{
        display: inline-block;
        margin-top: 30px;
        margin-bottom: 30px;
    }
    .product-b{
        height: 619px;
        margin-bottom: 30px;
    }
    .prob-left{
        width: 224px;
        height: 619px;
        background: blue;
        float: left;
    }
    .prob-left img{
        width: 224px;
        height: 619px;
    }
    .prob-right{
        margin-left: 2px;
        width: 986px;
        height: 619px;
        float: right;
    }
    .prob-right ul{
        margin-bottom: 14px;
    }
    .prob-right-t ul li{
        width: 232px;
        height: 302px;
        margin-left: 14px;
        display: inline-block;
        background: white;
    }
    .prob-right-t ul li .a span{
        display: inline-block;
        background:  #7ECF68;;
        width: 67px;
        height: 24px;
    }
    .prob-right-t ul li .a  a{
        width: 190px;
        height: 194px;
        display: inline-block;
        
    }
    .prob-right-t ul li .a  a img{
        width: 200px;
        height: auto;
        margin-top: 20px;
    }
    .prob-right-t ul li .a .itn{
        color: #333333;
        font-size: 14px;
        font-weight: bolder;
    }
    .prob-right-t ul li .a .its{
        margin-top: 6px;
    }
    .prob-right-t ul li .a .itp{
        margin-bottom: 30px;
        margin-top: 13px;
    }
    .prob-right-b ul li{
        width: 232px;
        height: 302px;
        margin-left: 14px;
        display: inline-block;
        background: white;
    }
    .prob-right-b ul li .a span{
        display: inline-block;
        background:  #7ECF68;;
        width: 67px;
        height: 24px;
    }
    .prob-right-b ul li .a  a{
        width: 190px;
        height: 194px;
        display: inline-block;
        
    }
    .prob-right-b ul li .a  a img{
        width: 200px;
        height: auto;
        margin-top: 20px;
    }
    .prob-right-b ul li .a .itn{
        color: #333333;
        font-size: 14px;
        font-weight: bolder;
    }
    .prob-right-b ul li .a .its{
        margin-top: 6px;
    }
    .prob-right-b ul li .a .itp{
        margin-bottom: 30px;
        margin-top: 13px;
    }
</style>