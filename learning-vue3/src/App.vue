<template>
	<div>
		<ul>
			<template v-for="(item, index) in eventItems" :key="item.id">
				<!--				<li v-if="item.id % 2 === 0">-->
				<li>ID: {{ item.id }} 인덱스: {{ index }},{{ item.message }}</li>
			</template>
		</ul>
	</div>
</template>

<script>
import { computed, reactive } from 'vue';

export default {
	setup() {
		const items = reactive([
			{ id: 1, message: 'Java' },
			{ id: 2, message: 'HTML' },
			{ id: 3, message: 'CSS' },
			{ id: 4, message: 'JavaScript' },
		]);

		const eventItems = computed(() => items.filter(item => item.id % 2 === 0));
		return { items, eventItems };
	},
};
</script>

<style lang="scss" scoped></style>
