<template>
	<div>
		<LabelInput
			:model-value="firstName"
			@update:model-value="value => $emit('update:firstName', value)"
			label="성"
		></LabelInput>
		<LabelInput
			:model-value="lastName"
			@update:model-value="value => $emit('update:lastName', value)"
			label="이름"
		></LabelInput>
	</div>
</template>

<script>
import LabelInput from './LabelInput.vue';

export default {
	props: ['firstName', 'lastName'],
	emits: ['update:firstName', 'update:lastName'],
	components: {
		LabelInput,
	},
	setup() {
		return {};
	},
};
</script>

<style lang="scss" scoped></style>
