<script>
export default {
	emits: ['funProps1', 'funProps2'],
	props: {
		name: String,
		salary: Number,
		age: Number,
	},

	data() {
		return {
		}
	},
	methods: {
		funcProps11: function () {
			this.$emit('funProps1')
		},
		funcProps22: function () {
			this.$emit('funProps2')
		}
	}
}
</script>

<template>
	<ul>
		<li>Name: {{ name }}</li>
		<li>Salary: {{ salary }}</li>
		<li>Age: {{ age }}</li>
	</ul>
	<button @click="funcProps11">alert1</button>
	<button @click="funcProps22">alert2</button>
</template>
