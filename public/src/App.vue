<template>
  <div id="app">
    <v-nav class="main-nav">
      <a href="#!" class="brand-logo" slot="logo"><router-link to="/"><img src="./assets/logo-white.png"></router-link></a>
      <ul class="right">
        <li>
          <router-link to="/order">주문</router-link>
        </li>
        <li>
          <a href="#!" v-side-nav:demo><v-icon>shopping_cart</v-icon></a>
        </li>
      </ul>
      <v-side-nav id="demo">
        <ul>
          <li>호호</li>
          <li>호호</li>
          <li>호호</li>
        </ul>
      </v-side-nav>
    </v-nav>
      <router-view></router-view>
  </div>
</template>

<script>
  import Vue from "vue"
  import VueRouter from 'vue-router'
  import Materials from "vue-materials"
  Vue.use(VueRouter)
  Vue.use(Materials);

  import Order from './components/Order.vue'
  import Home from './components/Home.vue'

  const routes = [
    { path: '/', component: Home },
    { path: '/order', component: Order },
  ];

  const router = new VueRouter({routes});

  export default {
    name: 'app',
    router,
    data () {
      return {
        msg: 'Welcome to Your Vue.js App',
      }
    }
  }
</script>

<style lang="scss">
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
  }
  .brand-logo {
    img {
      height: 25px;
    margin-bottom: 4px;
    }
    
  }
  .main-nav {
    nav {
      background: #00acc1;
    }
  }
</style>
