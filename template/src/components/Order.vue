<template lang="html">
	<div>
		<div>
            <p> 대여정보 확인 </p>
        </div>
		<div class="o-card">
			<v-card style="overflow: hidden;">
				<div class="o-imgspace">
		      		<div class="o-img">
		      			<a>book1</a>
		      		</div>
		      		<div class="o-img">
		      			<a>book2</a>
		      		</div>
		      		<div class="o-img">
		      			<a>book3</a>
		      		</div>
		      		<div class="o-img">
		      			<a>book4</a>
		      		</div>
		      	</div>
		        <div class="o-total">
		            <p> Total Textbook : 4 </p>
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
			<p> 구매자 </p>
		</div>
		<div class="p-input">
			<div class="input-field">
            <v-text-input name="name"
                        id="name"
                        placeholder="홍길동"
            ></v-text-input>
        	</div>
    	</div>

    	<div>
			<p> 카드번호 </p>
		</div>
		<div class="p-input">
			<div class="input-field">
            <v-text-input name="cardNum"
                        id="cardNum"
                        placeholder="0000-0000-0000-0000"
            ></v-text-input>
        	</div>
    	</div>

    	<div>
			<p> CVC </p>
		</div>
		<div class="p-input">
			<div class="input-field">
            <v-text-input name="cardCVC"
                        id="cardCVC"
                        placeholder="****"
            ></v-text-input>
        	</div>
    	</div>

    	<div>
			<p> 이용기간 </p>
		</div>

    	<div>
			<p> 결제금액 : 30,000원 </p>
		</div>

	</div>
	<div>
		<v-btn>대여</v-btn>
	</div>
		</div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {

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
	width: 100px;
	float:left;
	margin: 10px;
}

</style>
