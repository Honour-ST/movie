<template>
  <div id="app">
    <AppHeader v-show="showHeader" :showBack="showBack" :title="title"></AppHeader>
    <transition name='fade'>
      <router-view :city="city" @update-payorder="updatePayOrder"></router-view>
    </transition>
    <AppTabBar v-show="showTab" :loginStatus="loginStatus" @custom-update-title="updateTitle"></AppTabBar>
  </div>
</template>

<script>
import AppHeader from './components/AppHeader'
import AppTabBar from './components/AppTabBar'

export default {
  name: 'app',
  provide () {
    return {
      app: this
    }
  },
  data() {
    return {
      title:'猫眼电影',
      city:'广州',
      showHeader:true,
      showTab:true,
      showBack:false,
      loginStatus:false,
      payOrders:[]
    };
  },
  computed: {
    unread() {
      return this.payOrders.length ;
    }
  },
  methods: {
    // 更新标题
    updateTitle(title){
      this.title = title;
    },
    updatePayOrder(orderInfo){
      this.payOrders.push(orderInfo)
    }
  },
  components:{
    AppHeader,
    AppTabBar
  },
}
</script>

<style lang="less">

</style>
