<template lang="html">
<div>

	<div>
		<div>
			<p> 대여정보 확인 </p>
		</div>
		<div>
			<p> $plan-info </p>
		</div>
		<div>
			<p> 선택삭제 </p>
		</div>
	</div>

	<div>
		<!-- Menu -->
		<div>
			<div class="input-field">
	            <v-checkbox name="checkbox3"
	                      id="checkbox3"
	                      filled-in
	                      checked
	            ></v-checkbox>
	        </div>
			<div>
				<p> 도서정보 </p>
			</div>
			<div>
				<p> 배송비 </p>
			</div>
			<div>
				<p> 도착예정일 </p>
			</div>
			<div>
				<p> 대여기간 </p>
			</div>
		</div>

		<!-- item -->
		<div>
			<div class="input-field">
	            <v-checkbox name="checkbox3"
	                      id="checkbox3"
	                      filled-in
	                      checked
	            ></v-checkbox>
	        </div>
			<div>
				<p> 도서정보 </p>
			</div>
			<div>
				<p> 배송비 </p>
			</div>
			<div>
				<p> 도착예정일 </p>
			</div>
			<div>
				<p> 대여기간 </p>
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

.p-card {
    width: 380px;
	height: 580px;
	background-color: #ffffff;
	box-shadow: 2px 6px 8px 0 rgba(0, 0, 0, 0.1);
}

.p-input {
	margin: 0px 20px 20px 20px;
}

.test {
	background-color: #f7f7f7;
}

</style>
