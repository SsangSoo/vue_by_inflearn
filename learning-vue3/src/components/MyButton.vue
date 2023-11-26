<template>
	<div class="p-3 bg-danger">
		<!--    v-bind="$attrs"-->
		<button class="btn btn-primary" type="button" @click="sayHello">
			My Button
		</button>
		<!--    {{$attrs}}-->
	</div>
</template>

<script>
export default {
	emits: ['click'],
	// inheritAttrs: false,
	setup(props, { emit }) {
		// console.log('context.attrs : ', context.attrs);
		// console.log('class : ', context.attrs.class);
		// console.log('id : ', context.attrs.id);
		// console.log('onClick : ', context.attrs.onClick);
		// context.attrs.onClick();
		const sayHello = () => {
			emit('click');
		};
		return { sayHello };
	},
};
</script>

<style lang="scss" scoped></style>
