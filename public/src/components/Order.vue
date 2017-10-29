<template lang="html">
	<div>
		<div class="payment-done">
			<img src="./book.jpg">
		<h5>Payment</h5>
		<p>First step and also a final step</p>
	</div>
		<div class="o-card">
			<v-card style="overflow: hidden;  padding: 0.5rem 1.5rem;">
				<h4 class="sub-header">Confirm books</h4>
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
		</div>
    <div class= "p-box">
		<v-card style="overflow: hidden;  padding: 0.5rem 1.5rem;">
    	<div>
	    	<h4 class="sub-header"> Payment Method </h4>
	    </div>
	   <div>
			<p> 3 Months PLAN </p>
		</div>
		<div>
			<p>Name</p>
		</div>
		<div class="p-input">
			<div class="input-field">
            <v-text-input name="name"
                        id="name"
                        placeholder="홍길동"
                        length="string"
            ></v-text-input>
        	</div>
    	</div>

    	<div class="p-inputspace">
	    	<div>
				<p> Card Number </p>
			</div>
			<div class="p-num">
				<div class="input-field">
	            <v-text-input name="cardNum"
	                        id="cardNum"
	                        v-model="cardNum"
	                        placeholder="0000"
	                        type="password"
	                        maxlength="4"
	            ></v-text-input>
	        	</div>
	    	</div>

	    	<div class="p-dddd">
			<p> ㅡ </p>
			</div>

	    	<div class="p-num">
				<div class="input-field">
	            <v-text-input name="cardNum"
	                        id="cardNum"
	                        v-model="cardNum"
	                        placeholder="0000"
	                        type="password"
	                        maxlength="4"
	            ></v-text-input>
	        	</div>
	    	</div>

	    	<div class="p-dddd">
			<p> ㅡ </p>
			</div>

	    	<div class="p-num">
				<div class="input-field">
	            <v-text-input name="cardNum"
	                        id="cardNum"
	                        v-model="cardNum"
	                        placeholder="0000"
	                        type="password"
	                        maxlength="4"
	            ></v-text-input>
	        	</div>
	    	</div>

	    	<div class="p-dddd">
			<p> ㅡ </p>
			</div>

	    	<div class="p-num">
				<div class="input-field">
	            <v-text-input name="cardNum"
	                        id="cardNum"
	                        v-model="cardNum"
	                        placeholder="0000"
	                        type="password"
	                        maxlength="4"
	            ></v-text-input>
	        	</div>
	    	</div>

	    	<div class="p-num">
				<div class="input-field">
	            <v-text-input name="cardNum"
	                        id="cardNum"
	                        v-model="cardNum"
	                        placeholder="00"
	                        type="number"
	                        maxlength="2"
	            ></v-text-input>
	        	</div>
	    	</div>

	    	<div class="p-dddd">
			<p> / </p>
			</div>

	    	<div class="p-num">
				<div class="input-field">
	            <v-text-input name="cardNum"
	                        id="cardNum"
	                        v-model="cardNum"
	                        placeholder="0000"
	                        type="number"
	                        maxlength="4"
	            ></v-text-input>
	        	</div>
	    	</div>

    	</div>

    	<div>
			<p> CVC </p>
		</div>
		<div class="p-input">
			<div class="input-field">
            <v-text-input name="cardCVC"
                        id="cardCVC"
                        placeholder="***"
                        type="password"
                        maxlength="3"
            ></v-text-input>
        	</div>
    	</div>
    	<div>
			<p> Total Price : $30 </p>
		</div>
	</v-card>
		<div class="complete-payment">
			<router-link to="/order/complete"><v-btn>Confirm Payment</v-btn></router-link>
		</div>
	</div>
	
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
	// height: 200px;
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
	text-align: left;
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

.p-ddddd {
	color: #ffffff;
	margin: 20px 0px 0px 0px;
}

.cart-item {
    display: inline-block;
	    margin-right: 1.2rem;
		width: 130px;
	img {
		width: 100px;
	}
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
	img {
		    width: 10rem;
    margin-top: 1rem;
    margin-left: 4rem;
	}
}
.complete-payment {
	    text-align: right;
	button {
		    height: 50px;
    line-height: 50px;
    background: #ffbd19;
    font-weight: bolder;
	}
}
.sub-header {
	font-weight: 900;
    font-size: 1.8rem;
}

</style>
