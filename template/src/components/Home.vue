<template lang="html">
  <div>
    <section class="intro-section">
      <h1>전공서적, 한 학기 쉽게 빌리자!</h1>
      <div class="search-section">
        <input type="text" name="search" placeholder="도서명/ISBN 검색">
      </div>
      
    </section>
    <section class="book-list-section">
       <v-row>
         <v-grid s6 m4 v-for="(bookItem, index) in bookList" :key="bookItem.title">
           <BookItem v-bind:bookData="bookItem"></BookItem>
        </v-grid>
      </v-row>

      
    </section>
    
  </div>
</template>

<script>
import BookItem from './BookItem.vue'
export default {
    data () {
      return {
        msg: 'Welcome to Your Vue.js App',
        bookList: [
          {title: '전공서적1', imageUrl: 'https://s3.amazonaws.com/titlepages.leanpub.com/vuejs2-korean/hero?1485448142'},
          {title: '전공서적2', imageUrl: 'http://www.acornpub.co.kr/image/book/nd/hx/1494927544fPzhoVnU.jpg'},
          {title: '전공서적3', imageUrl: 'http://www.acornpub.co.kr/image/book/nd/hx/1494927544fPzhoVnU.jpg'}
        ]
      }
    },
  methods: {

  },
    components: {
      BookItem: BookItem,
    }
  
}
</script>
