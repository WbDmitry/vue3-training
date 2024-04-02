<script>
export default {
	props: {
		name: String,
		salary: Number,
		age: Number,
	},

	data() {
		return {
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
</template>
