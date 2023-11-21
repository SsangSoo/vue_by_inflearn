<template>
	<div>
		<p>{{ message }}</p>
		<p>{{ reverseMessage }}</p>
	</div>
</template>

<script>
import { ref, watch } from 'vue';

export default {
	setup() {
		const message = ref('Hello Vue3');
		const reverseMessage = ref('');

		// 최초 즉시실행 다른 방법
		// const reverseFunction = newValue => {
		const reverseFunction = () => {
			console.log('즉시실행함!!');
			// reverseMessage.value = newValue.split('').reverse().join('');
			reverseMessage.value = message.value.split('').reverse().join('');
		};

		watch(
			message,
			reverseFunction,
			// newValue => {
			// 	console.log('즉시실행함!!');
			// 	reverseMessage.value = newValue.split('').reverse().join('');
			// },
			// {
			// 	immediate: true, // 최초에 즉시실행
			// },
		);

		// reverseFunction(message.value); // 해당 최초실행은 watch에 의해 실행되는 게 아님. 매개변수를 따로 넣어줌.
		reverseFunction(); // 위의 라인 다른 방법 매개변수를 없앤다. 18번, 21번 라인 참고

		return { message, reverseMessage, reverseFunction };
	},
};
</script>

<style lang="scss" scoped></style>
