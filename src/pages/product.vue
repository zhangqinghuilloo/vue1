<template>
    <div class="product">
    <ProductParam v-bind:title="product.name"></ProductParam>
    <div class="pro-bt"></div>
    <div class="pro-text">
        <img src="/imgs/product/product-bg-2.png">
    </div>
    <div class="pro-bb"></div>
    <div class="pro-swiper">
        <swiper ref="mySwiper" :options="swiperOptions">
            <swiper-slide v-for="(item,index) in slideList" v-bind:key="index">
                <img v-bind:src="item.img">
            </swiper-slide>
            
            <div class="swiper-pagination" slot="pagination"></div>
          </swiper>
    </div>
    <div class="pro-video">
        
        <p class="pv-one">
            60帧超慢动作摄影<br>慢慢回味每一瞬间的精彩
        </p>
        <p class="pv-two">
            后置960帧电影般超慢动作视频，将眨眼间的美妙展现得淋漓尽致！ <br>更能AI 精准分析视频内容，15个场景智能匹配背景音效。
        </p>
        <div class="video">
            <video src="/imgs/product/video.mp4" controls="controls"></video>
        </div>
    </div>
    </div>
</template>
<script>
import ProductParam from './../components/ProductParam'
import { Swiper, SwiperSlide, directive } from 'vue-awesome-swiper'
import 'swiper/css/swiper.css'
    export default{
        name:'product',
        data(){
            return{
                product:{},
                swiperOptions: {
                    autoplay:true,
                    loop : true,
                     slidesPerView:3,
                    spaceBetween: 19,
                     freeMode: true,
                    pagination: {
                         el: '.swiper-pagination',
                         clickable :true
                    },
            
                },
                slideList:[
                    {
                     img: '/imgs/product/gallery-2.png'  
                    },{
                        img: '/imgs/product/gallery-3.png' 
                    },{
                        img: '/imgs/product/gallery-4.png' 
                    },{
                        img: '/imgs/product/gallery-5.jpg' 
                    },{
                        img: '/imgs/product/gallery-6.jpg' 
                    }
                ]
            }
        },
        components:{
            ProductParam,
            Swiper,
            SwiperSlide
        },
        directives: {
            swiper: directive
        },
        mounted(){
            this.getProductInfo();
        },
        methods:{
            getProductInfo(){
                let id=this.$route.params.id;
                this.axios.get(`/products/${id}`).then((res)=>{
                    this.product=res;
                })
            }
        }
    }
</script>
<style lang="scss">
    .pro-bt{
        height: 500px;
        background: url(/imgs/product/product-bg-1.png) no-repeat center;
    }
    .pro-text{
        height: 397px;
        margin:38px 0;
    }
    .pro-text img{
        width: 100%;
        height: 397px;
    }
    .pro-bb{
        height: 500px;
        background: url(/imgs/product/product-bg-3.png) no-repeat center;
    }
    
   .product .pro-swiper .swiper-container img{
        width: 100%;
        height: 100%;
    }
    .pro-video{
        background: black;
        height: 962px;
        text-align: center;
        position: relative;
    }
    .pv-one{
        color:#FFFFFF;
        font-size: 60px;
        font-weight: bolder;
        padding-top: 82px;
    }
    .pv-two{
        color:#FFFFFF;
        font-size: 24px;
        margin-top: 47px;
        
    }
    .video{
        width: 800px;
        height: 400px;
        position: absolute;
        top: 50%;
        left: 50%;
        margin-top: -50px;
        margin-left: -400px;
        border: 1px solid white;
    }
    .video video{
        width: 800px;
        height: 400px;
    }
</style>