<template>
    <div id="app">
            <!-- <scroller style="top: 44px"
            :on-refresh="refresh"
            :on-infinite="infinite">
          </scroller> -->
           <!-- <transition name="move" mode="out-in">
                    <keep-alive :include="tagsList">
                         <router-view></router-view>
                    </keep-alive>
                </transition> -->
            <router-view></router-view>
        <!-- <Tabbar></Tabbar> -->
    </div>
</template>
<style>
    /*@import "../static/css/color-dark.css";*/
    /*深色主题*/
    /*@import "../static/css/theme-green/color-green.css";   浅绿色主题*/
    /*@import "../static/css/main.css";*/
</style>
<script>
    import Tabbar from './components/common/Tabbar'
    import VueScroller from 'vue-scroller'
    Vue.use(VueScroller)
    export default {
        name: 'app',
        created: function() {
            this.$router.push('/')
        },
        components: {
            Tabbar
        },
        created() {
          
        },  
        methods: {
          
        },
    }
</script>