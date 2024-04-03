<script>
export default {
	emits: [
		'funProps1',
		'funProps2',
		'changeUser'
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
		funcProps11: function () {
			this.$emit('funProps1', '3333')
		},
		funcProps22: function () {
			this.$emit('funProps2', '25252352', '52364326')
		},

		saveUser: function () {
			this.isEdit = false
			this.$emit('changeUser', this.id, this.newName, this.newSalary, this.newAge)
		},

		editUser: function () {
			this.isEdit = true
		}
	}
}
</script>

<template>
	<template v-if="!isEdit">
		<ul>
			<li>Name: {{ name }}</li>
			<li>Salary: {{ salary }}</li>
			<li>Age: {{ age }}</li>
		</ul>
		<button @click="editUser">Редактировать</button>
	</template>
	<template v-else>
		<input type="text" v-model="newName">
		<input type="number" v-model="newSalary">
		<input type="number" v-model="newAge">
		<button @click="saveUser">Сохранить</button>
	</template>
</template>
