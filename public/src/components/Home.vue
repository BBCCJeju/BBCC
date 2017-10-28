<template lang="html">
  <div>
    <section class="intro-section">
      <v-container>
      <div class="intro">
        <p>한 학기동안 3만원으로 전공서적을 6권까지 대여해보세요.</p>
        <p>바보카코는 전공서적 대여 서비스를 통해 종이 절약의 선순환 고리를 만듭니다.</p>
      </div>
      <div class="search-container">
        <input v-model="keyword" type="text" name="search" placeholder="도서명/ISBN 검색">
        <div className="search-btn-container">
                  <v-icon>search</v-icon>
                </div>
      </div>
      </v-container>
    </section>
    <v-container>
    <section class="book-list-section">
       <v-row>
         <v-grid s6 m4 v-for="(bookItem, index) in bookList" :key="bookItem.title">
           <BookItem v-bind:bookData="bookItem"></BookItem>
        </v-grid>
      </v-row>
    </section>
    </v-container>
    
  </div>
</template>

<script>
import BookItem from './BookItem.vue'
import Vue from "vue"
import axios from "axios"
import _ from "lodash"

var VueFire = require('vuefire')
var config = {
        apiKey: "AIzaSyCkbXd5PtrE4_21Rf17vBlBaZUqU7smO0s",
        authDomain: "bbcc-410d8.firebaseapp.com",
        databaseURL: "https://bbcc-410d8.firebaseio.com",
        projectId: "bbcc-410d8",
        storageBucket: "bbcc-410d8.appspot.com",
        messagingSenderId: "790989195073"
};
    
var firebaseApp = firebase.initializeApp(config);
var Firebase = require('firebase')
Vue.use(VueFire)

function showBookList() {
  var bookArr = [];
  console.log("파베", firebaseApp.database())
  // bookArr = firebaseApp.database().ref('/books').find({});
  bookArr = firebaseApp.database().ref('/books/');
  console.log("ba", bookArr)
  return bookArr;
}




// showBookList();

export default {
  firebase: function () {
    return {
      bookList: firebaseApp.database().ref('/books/'),
      
    }
  },
  
  created() {
    this.getList();
    // axios.get('http://52.79.207.88:8000/book').then(data => {
    //     this.bookList = data.data;
    // });
  },
    data () {
      return {
        msg: 'Welcome to Your Vue.js App',
        bookList: '3',
        keyword: null,
      }
    },
    watch: {
    // 질문이 변경될 때 마다 이 기능이 실행됩니다.
    keyword: function (keyword) {
      console.log("입력중", keyword)
      // this.getSearchList(keyword);
      this.getAnswer();
      
    }
  },
  methods: {
    getList() {
      axios.get('http://52.79.207.88:8000/book').then(data => {
        this.bookList = data.data;
      });
    },
    getAnswer: _.debounce(
      function () {
        var vm = this
        axios.get('http://52.79.207.88:8000/book/search', {
          params: {
            keyword: vm.keyword
          }
        }).then(function (res) {
          console.log("검색완료", res)
            vm.bookList = res.data;
          });
      },
      500
    ),
    getSearchList: function(keyword) {

      _.debounce(function() {
        console.log("오에에", keyword)
        axios.get('http://52.79.207.88:8000/book/search', {
          params: {
            keyword: keyword
          }
        }).then(data => {
          this.bookList = data.data;
        })
      }, 5);
    }
  },
  components: {
    BookItem: BookItem,
    
  }
  
}
</script>
<style lang="scss">
  .intro-section {
    background-image: url("./landing-bg.jpg");
    margin-top: -15px;
    padding-bottom: 4rem;
    .intro {
      padding-top: 2rem;
    color: white;
    font-size: 1.2rem;
    p {
      margin: 3px;
    }
    }
    
  }

  .search-container {
  background: white;
  display: -webkit-flex;
  display: flex;
  height: 3.5rem;
  padding: 7px;
  position: relative;
  top: 22px;
  box-shadow: 0 15px 15px rgba(0, 0, 0, 0.02);
  input {
    -webkit-flex: 1;
    flex: 1;
    border: none;
        height: initial;
    margin: initial;
  }
  .search-btn-container {
    width: 50px;
    i {
      line-height: 2.7rem;
      float: right;
      color: red;
    }
  }

}
</style>
