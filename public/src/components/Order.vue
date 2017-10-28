<template lang="html">
	<div>
		<div>
            <p> 대여정보 확인 </p>
        </div>
		<div class="o-card">
			<v-card style="overflow: hidden;">
				<div class="o-imgspace">
					<div class="cart-item" v-for="(bookItem, index) in bookList" :key="bookItem.title">
						<img :src="JSON.parse(bookItem).img" />
					</div>
		      	</div>
		        <div class="o-total">
		            <p> Total Textbook : </p>
		        </div>
		    </v-card>
		</div>
    <div class= "p-box">
    	<div>
	    	<h4> Payment Method </h4>
	    </div>
	   <div>
			<p> 3개월 PLAN 구매 </p>
		</div>
		<div>
			<p> 이름 </p>
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
				<p> 카드번호 </p>
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
			<p> 이용기간 </p>
		</div>

    	<div>
			<p> 결제금액 : $30 </p>
		</div>

	</div>
	<div>
		<router-link to="/order/complete"><v-btn>대여</v-btn></router-link>
	</div>
		</div>
    </div>
  </div>
</template>

<script>
import BookItem from './BookItem.vue'

export default {
	created() {
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
.p-inputspace {
    height: 120px;
}

.p-ddddd {
	color: #ffffff;
	margin: 20px 0px 0px 0px;
}

.cart-item {
    display: inline-block;
	img {
		width: 100px;
	}

}
.p-inputspace {
	height: 120px;
}

</style>
