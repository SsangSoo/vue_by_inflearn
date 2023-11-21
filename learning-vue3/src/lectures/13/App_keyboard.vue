<template>
	<div>
		<input type="text" @keyup.ctrl.enter="addTodo" />
		<!-- ctrl + enter -->
		<ul>
			<li v-for="(todo, index) in todos" :key="index">
				{{ todo }}
			</li>
		</ul>
	</div>
</template>

<script>
import { reactive } from 'vue';

export default {
	setup() {
		const todos = reactive([]);

		const addTodo = event => {
			if (event.key == 'Enter') {
				todos.push(event.target.value);
				event.target.value = '';
				event.target.focus();
			}
		};
		return { todos, addTodo };
	},
};
</script>

<style lang="scss" scoped></style>
