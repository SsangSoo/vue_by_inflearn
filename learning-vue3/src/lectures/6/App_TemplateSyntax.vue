<template>
	<div>
		<h2>보간법</h2>
		<p>{{ message }}</p>
		<p v-once>{{ message }}</p>
		<button v-on:click="message = message + '!'">Click!</button>
		<hr />
		<h2>HTML</h2>
		<p>{{ rawHtml }}</p>
		<p v-html="rawHtml"></p>
		<hr />
		<h2>속성 바인딩</h2>
		<div v-bind:title="dynamicTitle">
			마우스를 올려보세요. 마우스가 올라가면 보여요!
		</div>
		<input type="text" value="홍길동" v-bind:disabled="isInputDisabled" />
		<input v-bind="attr" />
		<h2>JavaScript</h2>
		{{ message.split('').reverse().join('') }} <br />
		{{ isInputDisabled ? '예' : '아니오' }}
	</div>
</template>

<script>
import { ref } from 'vue';

export default {
	setup() {
		const message = ref('안녕하세요!');
		const rawHtml = ref('<strong>안녕하세요</strong>');
		const dynamicTitle = ref('안녕하세요!!!!');
		const isInputDisabled = ref(true);

		const attr = ref({
			type: 'text',
			value: '12345678',
			disable: false,
		});

		return {
			message,
			rawHtml,
			dynamicTitle,
			isInputDisabled,
			attr,
		};
	},
};
</script>

<style lang="scss" scoped></style>
