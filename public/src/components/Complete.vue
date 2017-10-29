<template lang="html">
	<div>
		<div class="p-box">
					<img src="./trees.svg">
					<div class="payment-done">
						<h5>Yeah! You already finished.</h5>
						<p>You can check this in 'my-page'</p>
					</div>
        </div>
		<div class="o-card">
			<v-card style="overflow: hidden; padding: 0.5rem 1.5rem;">
				<h4 class="sub-header">Your book list</h4>
				<div class="o-imgspace">
					<div class="cart-item" v-for="(bookItem, index) in bookList" :key="bookItem.title">
						<img :src="JSON.parse(bookItem).img" />
						<p>{{JSON.parse(bookItem).title}}</p>
					</div>
		      		
		      	</div>
		        <div class="o-total">
		            <p> Total Textbook : {{bookList.length}}</p>
		        </div>

		    </v-card>

		    <div class="complete-payment">
		    	<router-link to="/"><v-btn>Go to main page</v-btn></router-link>
				</div>
		</div>
  </div>
</template>

<script>
import BookItem from './BookItem.vue'

export default {
	created() {
		window.scrollTo(0,0);
		this.bookList =  this.allStorage();
	},
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
		allStorage: function() {
      var values = [],
        keys = Object.keys(localStorage),
        i = keys.length;
        console.log("올스토", keys)
        while ( i-- ) {
          var item = localStorage.getItem(keys[i]);
          if(Number(keys[i])) {
            values.push( localStorage.getItem(keys[i]) );
          }
        }
        return values;
    }
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
		text-align: center;
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

.p-inputspace {
	height: 120px;
}

.payment-done {
	text-align: center;
	h5 {
		    font-weight: 800;
    font-size: 2.2rem;
	}
	p {
		    font-size: 1.2rem;
    margin: 0;
	}
}

.cart-item {
    display: inline-block;
	img {
		width: 100px;
	}
}

</style>
