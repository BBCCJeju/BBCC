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
//      axios.get('http://52.79.207.88:8000/book').then(data => {
  this.bookList = [{"isbn":1,"title":"Operating System Concepts, 9/E","description":"The ninth edition of Operating System Concepts continues to evolve to provide a solid theoretical foundation for understanding operating systems. This edition has been updated with more extensive coverage of the most current topics and applications, improved conceptual coverage and additional content to bridge the gap between concepts and actual implementations. A new design allows for easier navigation and enhances reader motivation. Additional end-of-chapter, exercises, review questions, and programming exercises help to further reinforce important concepts. WileyPLUS, including a test bank, self-check exercises, and a student solutions manual, is also part of the comprehensive support package.","img":"https://user-images.githubusercontent.com/3839771/32136277-a05aedae-bc45-11e7-9b5b-034286fa5b69.png","author":"Abraham Silberschatz, Peter B. Galvin, Greg Gagne","publisher":" John Wiley & Sons ","publishYear":2013,"createdAt":"2017-10-28T12:50:31.054Z","updatedAt":"2017-10-28T12:50:31.054Z","id":"59f47d17e61745e9250f7dcf"},{"isbn":2,"title":"Global Environment Outlook - 3","description":"https://user-images.githubusercontent.com/3839771/32136167-fbe7ed6c-bc44-11e7-86a6-6189a4260441.png","img":"https://user-images.githubusercontent.com/3839771/32136167-fbe7ed6c-bc44-11e7-86a6-6189a4260441.png","author":"United Nations Environment Programme","publisher":"Earthscan Publications","publishYear":2002,"createdAt":"2017-10-28T12:55:39.735Z","updatedAt":"2017-10-28T12:55:39.735Z","id":"59f47e4be61745e9250f7dd0"},{"isbn":3,"title":"The Cartoon Guide to the Environment","description":"For those who think the Ozone Hole is a grunge rock band or that the Green Revolution happened in Greenland, this helpful, often hilarious book provides the perfect introduction to the world of environmental literacy. From chemical cycles to life communities to food webs to pollution, deforestation, and global warming, Gonnick explains environmental concepts in layman's terms and explains their relevance and relationship to the planet's ecology. Cartoons throughout.","img":"https://images-na.ssl-images-amazon.com/images/I/51KIu18qMjL.jpg","author":"Alice Outwater","publisher":"Collins","publishYear":1996,"createdAt":"2017-10-28T12:57:38.184Z","updatedAt":"2017-10-28T12:57:38.184Z","id":"59f47ec2e61745e9250f7dd1"},{"isbn":4,"title":"The C Programming Language","description":"This book is meant to help the reader learn how to program in C. It is the definitive reference guide, now in a second edition. Although the first edition was written in 1978, it continues to be a worldwide best-seller. This second edition brings the classic original up to date to include the ANSI standard.","img":"https://www.edutechlearners.com/wp-content/uploads/2017/08/The-C-Programming-Language-by-Kernighan-Ritchie-PDF.png","author":"Brian W. Kernighan, Dennis Ritchie","publisher":"Prentice Hall","publishYear":1988,"createdAt":"2017-10-28T13:01:51.414Z","updatedAt":"2017-10-28T13:01:51.414Z","id":"59f47fbfe61745e9250f7dd2"},{"isbn":5,"title":"Overwatch: World Guide","description":"Welcome to the world of Overwatch! This handbook is the perfect introduction to the scientists, soldiers, and adventurers who make up the Overwatch roster, from the time-jumping Tracer to the super-smart, genetically engineered gorilla Winston. You'll discover each hero's story and which unique abilities and weapons they bring to the battlefront. Then learn about the Omnic Crisis and how humanity restored peace, and get to know the awesome environments that make up the Overwatch landscape. There's a poster you can hang on your wall, too!","img":"https://images-na.ssl-images-amazon.com/images/I/71eP7oMGrlL.jpg","author":"Terra Winters","publisher":"Scholastic","publishYear":2017,"createdAt":"2017-10-28T13:04:45.458Z","updatedAt":"2017-10-28T13:04:45.458Z","id":"59f4806de61745e9250f7dd3"},{"isbn":6,"title":"Weapons of Math Destruction","description":"The models being used today are opaque, unregulated, and incontestable, even when they're wrong. Most troubling, they reinforce discrimination. Tracing the arc of a person's life, O'Neil exposes the black box models that shape our future, both as individuals and as a society. These 'weapons of math destruction' score teachers and students, sort CVs, grant or deny loans, evaluate workers, target voters, and monitor our health.","img":"https://images-na.ssl-images-amazon.com/images/I/51eUw-v0X%2BL._SX329_BO1,204,203,200_.jpg","author":"Cathy O’Neil","publisher":"Penguin Group USA","publishYear":2017,"createdAt":"2017-10-28T13:06:53.587Z","updatedAt":"2017-10-28T13:06:53.587Z","id":"59f480ede61745e9250f7dd4"},{"isbn":7,"title":"Chaos Monkeys","description":"Imagine a chimpanzee rampaging through a data center powering everything from Google to Facebook. Infrastructure engineers use a software version of this “chaos monkey” to test online services’ robustness--their ability to survive random failure and correct mistakes before they actually occur. Tech entrepreneurs are society’s chaos monkeys, disruptors testing and transforming every aspect of our lives, from transportation (Uber) and lodging (Airbnb) to television (Netflix) and dating (Tinder). One of Silicon Valley’s most provocative chaos monkeys is Antonio Garcia Martinez.","img":"https://images-na.ssl-images-amazon.com/images/I/51FAKHDS4WL.jpg","author":"Antonio Garcia Martinez","publisher":"Ebury Press","publishYear":2017,"createdAt":"2017-10-28T13:09:03.634Z","updatedAt":"2017-10-28T13:09:03.634Z","id":"59f4816fe61745e9250f7dd5"},{"isbn":9,"title":"Barron's Ap Biology","description":"Barron’s AP Biology is one of the most popular test preparation guides around and a 'must-have' manual for success on the Biology AP Test.","img":"https://images-na.ssl-images-amazon.com/images/I/5162w4Q-M6L._SX258_BO1,204,203,200_.jpg","author":"Deborah T. Goldberg","publisher":"Barron's Educational Series","publishYear":2017,"createdAt":"2017-10-28T13:15:49.006Z","updatedAt":"2017-10-28T13:15:49.006Z","id":"59f48305e61745e9250f7dd7"},{"isbn":10,"title":"Gravitation","description":"First published in 1973, Gravitation is a landmark graduate-level textbook that presents Einstein’s general theory of relativity and offers a rigorous, full-year course on the physics of gravitation. Upon publication, Science called it “a pedagogic masterpiece,” and it has since become a classic, considered essential reading for every serious student and researcher in the field of relativity. This authoritative text has shaped the research of generations of physicists and astronomers, and the book continues to influence the way experts think about the subject.","img":"https://upload.wikimedia.org/wikipedia/en/b/b6/Gravitation_book.jpg","author":"Kip S. Thorne","publisher":"Princeton University Press","publishYear":2017,"createdAt":"2017-10-28T13:17:06.312Z","updatedAt":"2017-10-28T13:17:06.312Z","id":"59f48352e61745e9250f7dd8"},{"isbn":8,"title":"Principles of Fermentation Technology, 2/E ","description":"This second edition has been thoroughly updated to include recent advances and developments in the field of fermentation technology, focusing on industrial applications.","img":"https://images-na.ssl-images-amazon.com/images/I/41LThHVXg5L._AC_UL320_SR260,320_.jpg","author":"Peter F. Stanbury, A. Whitaker, S. Hall","publisher":"Butterworth-Heinemann","publishYear":1999,"createdAt":"2017-10-28T13:13:19.003Z","updatedAt":"2017-10-28T13:13:19.003Z","id":"59f4826fe61745e9250f7dd6"}]
//        this.bookList = data.data;
//      });
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
