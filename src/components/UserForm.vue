<script>
export default {
	emits: [
		'addUser',
	],
	props: {
		id: Number,
		name: String,
		salary: Number,
		age: Number,
	},

	data() {
		return {
			isEdit: false,
			newName: this.name,
			newSalary: this.salary,
			newAge: this.age,
		}
	},
	methods: {
		addUser: function () {
			this.$emit('addUser', this.newName, this.newSalary, this.newAge)
		}
	}
}
</script>

<template>
	<input type="text" placeholder="Name" v-model="newName">
	<input type="number" placeholder="Salary" v-model="newSalary">
	<input type="number" placeholder="Age" v-model="newAge">
	<button @click="addUser">Создать</button>
</template>