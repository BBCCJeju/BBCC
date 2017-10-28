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
	    	<a> Credit or Debit Cards </a>
	    </div>
	    <div>
	    	<a> Cards Number </a>
	    </div>
    	<div>
	    	<div class="p-num">
		    	<div class="input-field">
		            <v-text-input name="first"
		                        id="first"
		                        placeholder="XXXX"
		            ></v-text-input>
		        </div>
		    </div>
		    <div class="p-num">
		        <div class="input-field">
		            <v-text-input name="last"
		                        id="last"
		                        placeholder="XXXX"
		            ></v-text-input>
		        </div>
		    </div>
		    <div class="p-num">
		        <div class="input-field">
		            <v-text-input name="last"
		                        id="last"
		                        placeholder="XXXX"
		            ></v-text-input>
		        </div>
		    </div>
		    <div class="p-num">
		        <div class="input-field">
		            <v-text-input name="last"
		                        id="last"
		                        placeholder="XXXX"
		            ></v-text-input>
		        </div>
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
	height: 250px;
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
