<template lang="html">
<div>
	<div class="c-box">
		<v-card style="overflow: hidden;">

		<div>
			<p> 3개월 PLAN 구매 </p>
		</div>
		<div>
			<p> 구매자 </p>
		</div>
		<div class="c-input">
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
		<div class="c-input">
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
		<div class="c-input">
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

	    </v-card>
	</div>
	<div>
		<v-btn>구매</v-btn>
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

.c-box {
    margin: 100px 300px 50px 300px;
}

.c-input {
	margin: 0px 20px 20px 20px;
}

</style>
