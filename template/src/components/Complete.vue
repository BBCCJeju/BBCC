<template lang="html">
	<div>
		<div class="p-box">
            <h5> 도서 대여 신청이 완료되었습니다! </h5>
            <p> 해당 도서 목록은 마이페이지에서도 확인하실 수 있습니다. </p>
        </div>
		<div class="o-card">
			<v-card style="overflow: hidden;">
				<div class="o-imgspace">
		      		<li v-for="(bookItem, index) in bookList" :key="bookItem.title">
					    <BookItem v-bind:bookData="bookItem"></BookItem>
					</li>
		      	</div>
		        <div class="o-total">
		            <p> Total Textbook : </p>
		        </div>

		    </v-card>

		    <div class="p-box">
		    	<router-link to="/"><v-btn>홈으로 돌아가기</v-btn></router-link>
				</div>
		</div>
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
        ],
      }
    },
  methods: {

  },
    components: {
      BookItem: BookItem,
    }

}
</script>

<style lang="scss">

.o-card {
    margin: 0px 50px 50px 50px;
}

.o-imgspace {
	height: 200px;
}

.o-img {
	width: 100px;
	height: 200px;
	margin: 20px;
	float:left;
}

.o-total {
	margin: 20px;
	float: right;
}

.p-box {
    margin: 50px;
}

.p-num {
	width: 50px;
	float:left;
	margin: 10px;
}

.p-dddd {
	float:left;
	margin: 20px 0px 0px 0px;
}

.p-ddddd {
	color: #ffffff;
	float:left;
	margin: 20px 0px 0px 0px;
}

.p-inputspace {
	height: 120px;
}

</style>
