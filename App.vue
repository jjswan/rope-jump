<template>
	<div>
		<ul class="font-serif py-10">
			<li v-if="count1 < 21">
				양발모아뛰기
				<button class="btn btn-info" @click="increment1">
					{{ count1 }}
				</button>
			</li>
			<p>양발모아뛰기를 {{ count1 }} 번 성공했습니다.</p>
			<p v-if="(0 < count1) & (count1 < 11)">
				축하합니다. 양발모아뛰기 {{ level3 }}급을 달성했습니다.
			</p>
			<p v-if="(11 <= count1) & (count1 < 21)">
				축하합니다. 양발모아뛰기 {{ level2 }}급을 달성했습니다.
			</p>
			<p v-if="count1 >= 21" :class="winner">
				축하합니다. 양발모아뛰기 {{ level1 }}급을 달성했습니다.
			</p>
			<br />
			<li v-if="count2 < 21">
				외발뛰기
				<button class="btn btn-info" v-on:click="increment2">
					{{ count2 }}
				</button>
			</li>
			<p>외발뛰기를 {{ count2 }} 번 성공했습니다.</p>
			<p v-if="(0 < count2) & (count2 <= 10)">
				축하합니다. 외발뛰기 {{ level3 }}급을 달성했습니다.
			</p>
			<p v-if="(11 <= count2) & (count2 < 21)">
				축하합니다. 외발뛰기 {{ level2 }}급을 달성했습니다.
			</p>
			<p v-if="count2 >= 21" v-bind:class="winner">
				축하합니다. 외발뛰기 {{ level1 }}급을 달성했습니다.
			</p>
			<br />
			<li v-if="count3 < 16">
				걸어뛰기
				<button class="btn btn-info" v-on:click="increment3">
					{{ count3 }}
				</button>
			</li>
			<p>걸어뛰기를 {{ count3 }} 번 성공했습니다.</p>
			<p v-if="(0 < count3) & (count3 < 11)">
				축하합니다. 걸어뛰기 {{ level3 }}급을 달성했습니다.
			</p>
			<p v-if="(11 <= count3) & (count3 < 15)">
				축하합니다. 걸어뛰기 {{ level2 }}급을 달성했습니다.
			</p>
			<p v-if="count3 > 15" v-bind:class="winner">
				축하합니다. 걸어뛰기 {{ level1 }}급을 달성했습니다.
			</p>
			<br />
			<li v-if="count4 < 8">
				뒤로뛰기
				<button class="btn btn-info" v-on:click="increment4">
					{{ count4 }}
				</button>
			</li>
			<p>뒤로뛰기를 {{ count4 }} 번 성공했습니다.</p>
			<p v-if="(0 < count4) & (count4 < 5)">
				축하합니다. 뒤로뛰기 {{ level3 }}급을 달성했습니다.
			</p>
			<p v-if="(5 <= count4) & (count4 < 8)">
				축하합니다. 뒤로뛰기 {{ level2 }}급을 달성했습니다.
			</p>
			<p v-if="count4 >= 8" v-bind:class="winner">
				축하합니다. 뒤로뛰기 {{ level1 }}급을 달성했습니다.
			</p>
			<br />
			<!-- <p>최종 줄넘기 등급은 {{ min }} 입니다.</p> -->
		</ul>
	</div>
</template>

<script>
import { ref, computed } from 'vue';
export default {
	setup() {
		const count1 = ref(0);
		const count2 = ref(0);
		const count3 = ref(0);
		const count4 = ref(0);
		const level3 = ref(3);
		const level2 = ref(2);
		const level1 = ref(1);

		const increment1 = () => {
			count1.value++;
		};
		const increment2 = () => {
			count2.value++;
		};
		const increment3 = () => {
			count3.value++;
		};

		const increment4 = () => {
			count4.value++;
		};

		const winner = computed(() => {
			return {
				red: true,
				bold: true,
			};
		});
		return {
			count1,
			count2,
			count3,
			count4,
			increment1,
			increment2,
			increment3,
			increment4,
			level1,
			level2,
			level3,
			winner,
		};
	},
};
</script>

<style scoped>
.red {
	color: red;
}
.bold {
	font-weight: bold;
}
</style>

<!-- 최종 등급 넣기 할 수 있을까? -->
