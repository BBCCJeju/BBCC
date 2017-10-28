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
	            <v-checkbox name="all-checkbox"
	                      id="all-checkbox"
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
		<div id="app">
			<span v-for="n in 3">
				<div>
					<div class="input-field">
			            <v-checkbox name="checkbox"
			                      id="checkbox"
			                      filled-in
			                      checked
			            ></v-checkbox>
			        </div>
			        <div>
			        	tmp
			        </div>
				</div>
			</span>
		</div>



	</div>


</div>
</template>

<script>

</script>

<style lang="scss">


</style>
