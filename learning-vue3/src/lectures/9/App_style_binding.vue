<template>
	<div>
		<div :style="styleObject">
			Lorem ipsum dolor sit amet, consectetur adipisicing elit. Deleniti laborum
			quos veniam. Assumenda, consequatur cumque dicta dignissimos eos et
			impedit in iste laudantium maiores maxime modi reiciendis repellat tempore
			voluptatem!
		</div>
		<button v-on:click="fontSize--">-</button>
		<button v-on:click="fontSize++">+</button>
	</div>
</template>

<script>
import { computed, ref } from 'vue';

export default {
	setup() {
		// const styleObject = reactive({
		// 	color: 'red',
		// 	fontSize: '13px',
		// });

		const fontSize = ref(13);
		const styleObject = computed(() => {
			return {
				color: 'red',
				fontSize: fontSize.value + 'px',
			};
		});

		return {
			styleObject,
			fontSize,
		};
	},
};
</script>

<style lang="scss" scoped></style>
