<template>
	<div></div>
</template>

<script>
import { reactive, ref, watch } from 'vue';

export default {
	setup() {
		const x = ref(0);
		const y = ref(0);

		// Object타입의 반응형 테이터 감지
		const obj = reactive({
			count: 0,
		});

		// watch(
		// 	() => x.value + y.value,
		// 	(sum, oldValue) => {
		// 		console.log('sum : ', sum);
		// 		console.log('oldValue : ', oldValue);
		// 	},
		// );

		// 배열 타입으오
		// watch([x, y], ([newX, newY]) => {
		// 	console.log(newX, newY);
		// });
		console.log(typeof obj.count);
		// watch(
		// 	() => obj.count,
		// 	(newValue, oldValue) => {
		// 		console.log('newValue: ', newValue);
		// 	},
		// );
		// watch(obj, (newValue, oldValue) => {
		// 	console.log('newValue: ', newValue); // 둘 다
		// 	console.log('oldValue: ', oldValue); // 같은 객체를 가리킨다.
		// });

		const person = reactive({
			name: '홍길동',
			age: 30,
			hobby: '운동',
			obj: {
				count: 0,
			},
		});

		// watch(person, newValue => {
		// 	console.log('newValue: ', newValue);
		// });

		watch(
			() => person.obj,
			newValue => {
				console.log('newValue: ', newValue);
			},
		);
		return { x, y, obj, person };
	},
};
</script>

<style lang="scss" scoped></style>
