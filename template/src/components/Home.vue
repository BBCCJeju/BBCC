<template lang="html">
  <div>
    <h1>홈 화면</h1>
    <li v-for="(bookItem, index) in bookList" :key="bookItem.title">
        <BookItem v-bind:bookData="bookItem"></BookItem>
    </li>
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
          {title: '전공서적2', imageUrl: 'http://www.acornpub.co.kr/image/book/nd/hx/1494927544fPzhoVnU.jpg'}
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
