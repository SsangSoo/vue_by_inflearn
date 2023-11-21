<template>
	<div></div>
</template>

<script>
import { ref, watch } from 'vue';

export default {
	setup() {
		const x = ref(0);
		const y = ref(0);

		// Object타입의 반응형 테이터 감지

		// watch(
		// 	() => x.value + y.value,
		// 	(sum, oldValue) => {
		// 		console.log('sum : ', sum);
		// 		console.log('oldValue : ', oldValue);
		// 	},
		// );

		// 배열 타입으오
		watch([x, y], ([newX, newY]) => {
			console.log(newX, newY);
		});
		return { x, y };
	},
};
</script>

<style lang="scss" scoped></style>
