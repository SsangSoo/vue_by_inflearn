<template>
	<div>
		<div class="text" :class="{ active: isActive, 'text-danger': hasError }">
			텍스트입니다.
		</div>
		<button v-on:click="toggle">toggle</button>
		<button v-on:click="hasError = !hasError">toggleError</button>
	</div>
</template>

<script>
import { ref } from 'vue';

export default {
	setup() {
		const isActive = ref(true);
		const hasError = ref(false);

		const toggle = () => {
			isActive.value = !isActive.value;
		};

		return { isActive, toggle, hasError };
	},
};
</script>

<style scoped>
.active {
	font-weight: 900;
}

.text-danger {
	color: red;
}
</style>
