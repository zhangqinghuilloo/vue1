<template>
    <div class="ali-pay">
      <order-header title="订单扫码">
        <template v-slot:tip>
            温馨提示：请您根据二维码进行支付~
        </template>
    </order-header>
      <loading v-if="loading"></loading>
      <div class="form" v-html="content"></div>
    </div>
  </template>
  <script>
    import OrderHeader from './../components/OrderHeader'
    import Loading from './../components/Loading'
    export default{
      name:'alipay',
      components:{
        Loading,
        OrderHeader
      },
      data(){
        return {
          orderId:this.$route.query.orderId,
          content:'',
          loading:true
        }
      },
      mounted(){
        this.paySubmit();
      },
      methods:{
        paySubmit(){
          this.axios.post('/pay',{
            orderId:this.orderId,
            orderName:'Vue手机商城',
            amount:0.01,                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
            payType:1 
          }).then((res)=>{
            this.content = res.content;
            setTimeout(()=>{
              document.forms[0].submit();
            },100)
          })
        }
      }
    }
  </script>