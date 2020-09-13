<template>
    <div class="login">
        <div class="login-top">
            <div class="lt-logo"></div>
            <div class="lt-text">
                <p class="t">小米商城</p>
                <p class="b">让每个人都能享受科技的乐趣</p>
                
            </div>
        </div>
        <div class="login-main">
            <div class="lm-form">
                <div class="lf-one">
                    <h4 class="zq qa">账号登录</h4>
                    <h4 class="zq qq">|</h4>
                    <h4 class="zq qz">扫码登录</h4>
                </div>
                <div class="lf-two"><input type="text" placeholder="请输入账号" class="ltwo-input" v-model="username"></div>
                <div class="lf-three"><input type="password" placeholder="请输入密码" class="lthree-input" v-model="password"></div>
                <div class="lf-four"><a href="#" v-on:click="login">登录</a></div>
                <div class="lf-five">
                    <a href="#" class="aa" v-on:click="reqister">手机短信登录/注册</a>
                    <div class="zc">
                        <a href="#" class="bb">立即注册</a>
                        <h class="cc">|</h>
                        <a href="#" class="dd">忘记密码？</a>
                    </div>
                </div>
            </div>
        </div>
        <div class="login-bottom"></div>
    </div>
</template>
<script>
    export default{
        name:'login',
        data(){
            return{
                username:'',
                password:'',
                userId:''
            }
        },
        methods:{
            login(){
                let { username,password } = this;
                this.axios.post('/user/login',{
                    username,
                    password
                }).then((res)=>{
                    this.$cookie.set('userId',res.id,{expires:'1M'})
                    this.$store.dispatch('saveUserName',res.username);
                    this.$router.push('/index')
                })
            },
            reqister(){
                this.axios.post('/user/login',{
                    username:'zqh',
                    password:'zqh1997',
                    email:'806042361@qq.com'
                }).then(()=>{
                    alert('注册成功');
                })
            }
        }
    }
</script>
<style lang="scss">
    .login-top{
        height: 112px;
        background: #FFFFFF;
        line-height: 112px;
    }
    .lt-logo{
        width: 53px;
        height: 52px;
        background: url('/imgs/logo-mi.png') no-repeat center;
        background-size: contain;
        margin-top: 25px;
        margin-left: 391px;
        margin-bottom: 36px;
        float: left;

    }
    .lt-text{
        float: left;
        margin-left: 18px;
    }
    .t{
        height: 30px;
        margin-top: -15px;
        font-size: 25px;
        font-weight: bold;
    }
    .b{
        height: 20px;
        font-size: 10px;
    }
    .login-main{
        height: 580px;
        background:url('/imgs/login-bg.jpg') no-repeat center;
        position: relative;
    }
    .lm-form{
        width: 410px;
        height: 510px;
        background: #FFFFFF;
        position: absolute;
        top: 37px;
        right: 50px;
    }
    .zq{
        display: inline-block;
        margin-right: 35px;
        font-size: 24px;
    }
    .qq{
        color: #D8D8D8;
        
    }
    .qa{
        color: #FF6700;
    }
    .qz{
        color: #666666;
    }
    .lf-one{
        margin-left: 73px;
        margin-top: 40px;
    }
    .lf-two{
        margin-top: 49px;
    }
    .ltwo-input{
        width: 348px;
        height: 50px;
        margin-left: 31px;
        font-size: 14px;
        margin-bottom:20px;
        padding-left: 14px;
    }
    .lthree-input{
        width: 348px;
        height: 50px;
        margin-left: 31px;
        font-size: 14px;
        margin-bottom: 30px;
        padding-left: 14px;
    }
    .lf-four{
        width: 352px;
        margin-left: 31px;
        text-align: center;
        height: 50px;
        line-height: 50px;
        background: #FF6600;
        margin-bottom: 14px;
    }
    .lf-four a{
        color: #FFFFFF;
        font-size: 16px;
    }
    .lf-five{
        width: 352px;
        margin-left: 31px;
        overflow: hidden;
    }
    .aa{
        display: inline-block;
        color: #FF6700;
        font-size: 14px;
    }
    .zc{
        float: right;
    }
    .bb{
        color: #9A9A9A;
        font-size: 14px;
        margin-right: 1px;
        display: inline-block;
    }
    .cc{
        color: #9A9A9A;
        margin-right: 1px;
        display: inline-block;
    }
    .dd{
        color: #9A9A9A;
      
        display: inline-block;
    }
</style>