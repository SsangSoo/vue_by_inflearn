<template>
	<div>
		<div v-memo="[views]">
			<p>subscribers: {{ subscribers }}</p>
			<p>views: {{ views }}</p>
			<p>likes: {{ likes }}</p>
		</div>
		<button @:click="subscribers++">Subscribers++</button>
		<button @click="views++">Views++</button>
		<button @click="likes++">Likes++</button>
	</div>
	<div>
		<p>subscribers: {{ subscribers }}</p>
		<p>views: {{ views }}</p>
		<p>likes: {{ likes }}</p>
	</div>
</template>

<script>
import { ref } from 'vue';

export default {
	setup() {
		const subscribers = ref(4000);
		const views = ref(400);
		const likes = ref(2);
		return { subscribers, views, likes };
	},
};
</script>

<style lang="scss" scoped></style>
