<template lang="html">
  <section class="book-container">
    
    <div class="add-container">
      <span v-if="is_cart" v-on:click="removeCart" class="cart_added"><v-icon >check_circle</v-icon></span>
      <span v-else="is_cart" v-on:click="addCart" class="cart_add"><v-icon>add_circle</v-icon></span>
    </div>
    <img :src="bookData.img">
    <!-- <div class="book-img" :style="{ 'background-image': 'url(' + bookData.img + ')' }"></div> -->
    <div class="book-info">
      <div class="card-title">{{bookData.title}}</div>
      <div class="card-author">{{bookData.author}}</div>
      
    </div>
  </section>
</template>

<script>
export default {
  props: ['bookData'],
  created() {
    if(localStorage.getItem(this.bookData.isbn)) {
      this.is_cart = true;
    } else {
      this.is_cart = false;
    }
    
  },
  computed: {
    
  },
  data () {
      return {
        is_cart: false
      }
    },
  methods: {
    addCart: function(e) {
      console.log("카트 담김", e, this.bookData)
      localStorage.setItem(this.bookData.isbn, JSON.stringify(this.bookData));
      this.is_cart = true;
      this.$emit('increment');
    },
    removeCart: function(e) {
      console.log("카트 빠짐", e, this.bookData)
      localStorage.removeItem(this.bookData.isbn);
      this.is_cart = false;
      this.$emit('increment');
    }
  }
}
</script>
<style lang="scss">
  .book-container {
    margin-bottom: 1rem;
    img {
      width: 100%;
      max-height: 16.3rem;
      border-radius: 3px;
      box-shadow: 0 20px 20px rgba(0, 0, 0, 0.08);
    }
    .book-info {
      height: 3rem;
      .card-title {
        font-weight: 500;
    color: #444444;
        margin: 6px 0 1px;
      }
      .card-author {
        color: #747474;
      }
    }
    .add-container {
        position: relative;
      top: 2.7rem;
      z-index: 2;
      text-align: right;
      padding-right: 5px;
      cursor: pointer;
      span.cart_added {
        color: #00acc1;
      }
      span.cart_add {
        color: rgba(173, 173, 173, 0.76);
      }
      i {
        font-size: 2.2rem;
      }
    }
  }
</style>
