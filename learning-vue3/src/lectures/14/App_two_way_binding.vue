<template>
	<div>
		<h2>input value</h2>
		<!--		<input type="text" v-model.lazy="inputValue" />-->
		<!--		<input type="text" v-model.number="inputValue" />-->
		<input type="text" v-model.trim="inputValue" />
		<!--    :value="inputValue"-->
		<!--    @input="event => (inputValue = event.target.value)"-->
		<div>{{ inputValue }}</div>
		<div>{{ typeof inputValue }}</div>

		<h2>textarea value</h2>
		<textarea type="text" v-model="textAreaValue"></textarea>
		<!--			:value="textAreaValue"-->
		<!--			@input="event => (textAreaValue = event.target.value)"-->
		<div>{{ textAreaValue }}</div>

		<h2>checkbox value</h2>
		<label for="checkbox">{{ checkboxValue }}</label>
		<input
			type="checkbox"
			id="checkbox"
			v-model="checkboxValue"
			true-value="Yes"
			false-value="No"
		/>
		<!--			:checked="checkboxValue"-->
		<!--			@change="event => (checkboxValue = event.target.checked)"-->
	</div>

	<h2>radio value</h2>
	<label>
		<input type="radio" name="type" value="O" v-model="radioValue" />
		<!--			@change="event => (radioValue = event.target.value)"-->
		<!--			:checked="radioValue === 'O'"-->
		O형
	</label>
	<label>
		<input type="radio" name="type" value="A" v-model="radioValue" />
		<!--			:checked="radioValue === 'A'"-->
		<!--			@change="event => (radioValue = event.target.value)"-->
		A형
	</label>
	<label>
		<input type="radio" name="type" value="B" v-model="radioValue" />
		<!--      :checked="radioValue === 'B'"-->
		<!--			@change="event => (radioValue = event.target.value)"-->
		B형
	</label>
	<label>
		<input type="radio" name="type" value="AB" v-model="radioValue" />
		<!--			:checked="radioValue === 'AB'"-->
		<!--			@change="event => (radioValue = event.target.value)"-->
		AB형
	</label>
	<div>
		{{ radioValue }}
	</div>
	<h2>select value</h2>
	<select v-model="selectValue">
		<!--    :value="selectValue"-->
		<!--    @change="event => (selectValue = event.target.value)"-->
		<option value="html">HTML 수업</option>
		<option value="css">CSS 수업</option>
		<option value="JS">JS 수업</option>
	</select>
	<div>{{ selectValue }}</div>
	<h3>checkbox values</h3>
	<label>
		<input type="checkbox" value="html" v-model="checkboxValues" />
		HTML
	</label>
	<label>
		<input type="checkbox" value="css" v-model="checkboxValues" />
		CSS
	</label>
	<label>
		<input type="checkbox" value="js" v-model="checkboxValues" />
		JS
	</label>
	<div>{{ checkboxValues }}</div>
</template>

<script>
import { ref } from 'vue';

export default {
	setup() {
		const inputValue = ref('');
		const textAreaValue = ref('');
		const checkboxValue = ref('No');
		const radioValue = ref('O');
		const selectValue = ref('html');
		const checkboxValues = ref([]);
		return {
			inputValue,
			textAreaValue,
			checkboxValue,
			radioValue,
			selectValue,
			checkboxValues,
		};
	},
};
</script>

<style lang="scss" scoped></style>
