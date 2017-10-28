<template>
  <div id="app">
    <v-nav>
      <a href="#!" class="brand-logo" slot="logo">Logo</a>
      <ul class="right">
        <li>
          <a href="#!"><v-icon>done</v-icon></a>
        </li>
        <li>
          <a href="#!" v-side-nav:demo="nav"><v-icon>사이드</v-icon></a>
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
    <router-link to="/order">주문</router-link>
    <router-link to="/">홈</router-link>
    <router-view></router-view>

    <li v-for="(bookItem, index) in bookList" :key="bookItem.title">
        <BookItem v-bind:bookData="bookItem" v-on:clickBook="clickBook"></BookItem>
    </li>

    <h1>{{ msg }}</h1>
    
  </div>
</template>

<script>
  import Vue from "vue"
  import VueRouter from 'vue-router'
  import Materials from "vue-materials"
  Vue.use(VueRouter)
  Vue.use(Materials);
  import BookItem from './components/BookItem.vue'
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
    methods: {
      clickBook(bookItem, index) {
        console.log("하이", bookItem);
      }
    },
    data () {
      return {
        msg: 'Welcome to Your Vue.js App',
        bookList: [
          {title: '전공서적1', imageUrl: 'https://s3.amazonaws.com/titlepages.leanpub.com/vuejs2-korean/hero?1485448142'},
          {title: '전공서적2', imageUrl: 'http://www.acornpub.co.kr/image/book/nd/hx/1494927544fPzhoVnU.jpg'}
        ]
      }
    },
    components: {
      BookItem: BookItem,
    }
  }
</script>

<style lang="scss">
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }

  h1, h2 {
    font-weight: normal;
  }

  a {
    color: #42b983;
  }
</style>
