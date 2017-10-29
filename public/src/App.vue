<template>
  <div id="app">
    <v-nav class="main-nav">
      <a href="#!" class="brand-logo" slot="logo"><router-link to="/"><img src="./assets/logo-white.png"></router-link></a>
      <ul class="right">
        <li>
          <div id="example-2">
            <div v-if="userPhoto" class="avatar-container" >
              <img :src="userPhoto"/>
            </div>
          <a v-else v-on:click="firebaseLogin">Login</a>
            
          </div>
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
  Vue.use(VueRouter);
  Vue.use(Materials);

  import Order from './components/Order.vue'
  import Home from './components/Home.vue'
  import Plan from './components/Plan.vue'
  import MyPage from './components/MyPage.vue'
  import Rental from './components/Rental.vue'
  import Complete from './components/Complete.vue'

  const routes = [
    { path: '/', component: Home },
    { path: '/order', component: Order },
    { path: '/order/plan', component: Plan },
    { path: '/my-page', component: MyPage },
    { path: '/rental', component: Rental },
    { path: '/order/complete', component: Complete },
  ];

  const router = new VueRouter({routes});

  

  export default {
    name: 'app',
    created() {
      var that = this;
      function onAuthStateChanged(user) {
        if (user) {
          that.userPhoto = user.photoURL;
          console.log("후에에에 유저 있어", user.photoURL)
        }
      }
      firebase.auth().onAuthStateChanged(onAuthStateChanged);
    },
    router,
    data () {
      return {
        msg: 'Welcome to Your Vue.js App',
        userPhoto: ''
      }
    },
    methods: {
    firebaseLogin: function (event) {
      console.log("하이하이");
      var provider = new firebase.auth.GoogleAuthProvider();
      firebase.auth().signInWithPopup(provider);
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
      height: 20px;
      
      @media only screen and (min-width: 993px) {
        // margin-left: 2rem;  
      }
    }
    
  }
  .main-nav {
    nav {
      background: #00acc1;
      .nav-wrapper {
        
        margin: 0 auto;
        @media only screen and (min-width: 993px) {
        width: 70%;
      }
      }
    }
  }
  .avatar-container {
    img {
          width: 42px;
    border-radius: 50%;
    border: 1px solid white;
    margin-top: 10px;
        margin-right: 0.7rem;
    }
  }
</style>
