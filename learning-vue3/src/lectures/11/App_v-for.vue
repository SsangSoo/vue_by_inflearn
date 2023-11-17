<template>
	<div>
		<ul>
			<template v-for="(item, index) in evenItems" :key="item.id">
				<!--				<li v-if="item.id % 2 === 0">-->
				<li>ID: {{ item.id }} 인덱스: {{ index }},{{ item.message }}</li>
			</template>
		</ul>
		<hr />
		<url>
			<li v-for="(value, key, index) in myObject" :key="key">
				{{ key }}-{{ value }}-{{ index }}
			</li>
		</url>
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

		const myObject = reactive({
			title: '제목',
			author: '홍길동',
			publishedAt: '2023-11-17',
		});

		const evenItems = computed(() => items.filter(item => item.id % 2 === 0));
		return { items, evenItems, myObject };
	},
};
</script>

<style lang="scss" scoped></style>
