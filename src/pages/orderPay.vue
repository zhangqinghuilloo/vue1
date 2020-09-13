<template>
  <div class="order-pay">
    <order-header title="订单支付">
      <template v-slot:tip>
        <span>请谨防钓鱼链接或诈骗电话，了解更多</span>
      </template>
    </order-header>
    <div class="wrapper">
      <div class="container">
        <div class="order-wrap">
          <div class="item-order">
            <div class="icon-succ"></div>
            <div class="order-info">
              <h2>订单提交成功！去付款咯～</h2>
              <p>请在<span>30分</span>内完成支付, 超时后将取消订单</p>
              <p>收货信息：{{addressInfo}}</p>
            </div>
            <div class="order-total">
              <p>应付总额：<span>{{payment}}</span>元</p>
            </div>
          </div>
        </div>
        <div class="item-pay">
          <h3>选择以下支付方式付款</h3>
          <div class="pay-way">
            <p>支付平台</p>
            <div class="pay pay-ali" :class="{'checked':payType==1}" @click="paySubmit(1)"></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import OrderHeader from './../components/OrderHeader'
export default{
  name:'order-pay',
  data(){
    return {
      orderId:this.$route.query.orderNo,
      addressInfo:'',//收货人地址
      payType:'',//支付类型
      payment:0,//订单总金额
    }
  },
  components:{
    OrderHeader,
  },
  mounted(){
    this.getOrderDetail();
  },
  methods:{
    getOrderDetail(){
      this.axios.get(`/orders/${this.orderId}`).then((res)=>{
        let item = res.shippingVo;
        this.addressInfo = `${item.receiverName} ${item.receiverMobile} ${item.receiverProvince} ${item.receiverCity} ${item.receiverDistrict} ${item.receiverAddress}`;
        this.payment = res.payment;
      })
    },
    paySubmit(payType){
      if(payType == 1){
        window.open('/#/order/alipay?orderId='+this.orderId,'_blank');
      }
    },
    goOrderList(){
      this.$router.push('/order/list');
    }
  }
}
</script>
<style lang="scss">
  .wrapper{
      background-color:#F5F5F5;
      padding-top:30px;
      padding-bottom:61px;
}

.order-wrap{
        padding: 62px 50px;
        background-color: #fff;
        font-size:14px;
        margin-bottom:30px;
        height:120px
}
.item-order{
          display: flex;
          align-items: center;
}
.icon-succ{
            width: 90px;
            height: 90px;
            border-radius: 50%;
            background:url('/imgs/icon-gou.png') #80c58a no-repeat center;
            background-size:60px;
            margin-right:40px;
          }
.order-info{
            margin-right: 248px;
}
.order-info h2{
              font-size:24px;
              color:#333333;
              margin-bottom:20px;
            }
.order-info p{
              color:#666666;
}
.order-info span{
                color:#FF6700;
              }
.order-total p:first-child{
              margin-bottom:30px;
            }
.order-total span{
              font-size:28px;
              color:#FF6700;
            }
.item-pay{
        padding:26px 50px 72px;
        background-color:#ffffff;
        color: #333333;
}
.item-pay h3{
          font-size: 20px;
          font-weight: 200;
          color: #333333;
          padding-bottom: 24px;
          border-bottom: 1px solid #D7D7D7;
          margin-bottom: 26px;
        }
.pay-way{
          font-size:18px;
}
.pay-way .pay{
            display:inline-block;
            width:188px;
            height:64px;
            border:1px solid #D7D7D7;
            cursor:pointer;
}
.pay-way .pay .checked{
              border:1px solid #FF6700;
            }
.pay-ali{
            background:url('/imgs/pay/icon-ali.png') no-repeat center;
            background-size:103px 38px;
            margin-top:19px;
          }
</style>