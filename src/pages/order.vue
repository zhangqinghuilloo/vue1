<template>
    <div>
        <router-view></router-view>
        <ServiceBar></ServiceBar>
        <nav-footer></nav-footer>
    </div>
</template>
<script>
    import ServiceBar from './../components/ServiceBar'
    import NavFooter from './../components/NavFooter'
    export default{
        name:'order',
        data(){
            return{

            }
        },
        components:{
            
            ServiceBar,
            NavFooter
        }
    }
</script>