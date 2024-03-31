<script>
export default {
	name: 'App',
	data() {
		return {
			firstName: 'Dmitry',
			lastName: 'Wb',
			linkText: 'Yandex поиск',
			href: 'https://ya.ru',
			num1: 10,
			num2: 6,
			arr: [1, 2, 3],
			obj: { x: 1, y: 2, z: 3 },
			textParagraph: 'Что такое Lorem Ipsum?',
			cost: 2000,
			amount: 1,
			visible: true,
		}
	},

	computed: {
		price: function () {
			return this.cost * this.amount
		}
	},

	methods: {
		getCurrentDate: function () {
			let currentDate = new Date();
			alert(currentDate)
		},

		getUserInfo: function () {
			alert(`User: ${this.lastName}.${this.firstName}`)
		},

		getDayAlerts: function () {
			let numDay = this.getDayOfTheWeek(
				Number(
					prompt("Введите число от 1 до 7")
				)
			);
			alert(numDay)
		},

		getDayOfTheWeek: function (day) {
			// let days = ['Понедельник', 'Вторник', 'Среда', 'Четверг', 'Пятница', 'Суббота', 'Воскресенье']
			// return days[day - 1]

			switch (day) {
				case 1: return "Понедельник"
				case 2: return "Вторник"
				case 3: return "Среда"
				case 4: return "Четверг"
				case 5: return "Пятница"
				case 6: return "Суббота"
				case 7: return "Воскресенье"
				default: return "Вы ввели неправильное число"
			}
		},

		outputTheSquareOfNumber: function (num) {
			return alert(num ** 2);
		},

		switchTextP: function (newText) {
			this.textParagraph = newText
		},

		setCost: function (params) {
			this.cost = params
		},

		setVisible: function () {
			this.visible = !this.visible
		},
	}
}
</script>

<template>
	<p>Что такое Lorem Ipsum?</p>
	{{ lastName }}
	{{ firstName }}
	<a v-bind:href="href" target="_blank">{{ linkText }}</a>
	<a :href="href" target="_blank">{{ linkText }}</a>
	{{ num1 ** 2 }}
	{{ num1 + num2 }}
	<p>Вывод каждого числа: {{ arr[0] }},{{ arr[1] }}, {{ arr[2] }}</p>
	<p>Сумма чисел: {{ arr[0] + arr[1] + arr[2] }}</p>
	<p>Ввывод содержимого объекта (способ 1): {{ obj.x + obj.y + obj.z }}</p>
	<p>Ввывод содержимого объекта (способ 2): {{ obj['x'] + obj['y'] + obj['z'] }}</p>
	<!-- {{ getCurrentDate() }} -->
	<button @click="getCurrentDate">Вывести дату по клику</button>
	<button @mouseover="getCurrentDate">Вывести дату при наведении</button>
	<button @click="getUserInfo">Вывести свойсва из data</button>
	<button @click="getDayAlerts">Узнать день недели</button>
	<button @click="outputTheSquareOfNumber(2)">Вывести квадрат числа 2</button>
	<button @click="outputTheSquareOfNumber(3)">Вывести квадрат числа 3</button>
	<p>{{ textParagraph }}</p>
	<button @click="switchTextP('Один текст')">Изменить текст на «Один текст»</button>
	<button @click="switchTextP('Второй текст')">Изменить текст на «Второй текст»</button>

	<p>Cost: {{ cost }}</p>
	<p>Amount: {{ amount }}</p>
	<p>Price: {{ price }}</p>
	<button @click="setCost(3250)">Изменить Cost на 3250</button>
	<button @click="setCost(2000)">Изменить Cost на 2000</button>
	<button @click.once="amount++">Amount++(once)</button>
	<a @click.prevent :href="href" target="_blank">{{ linkText }}</a>

	<p v-if="visible">Visible: true</p>
	<p v-if="!visible">Visible: false</p>
	<button @click="setVisible()">Visible: {{ visible }}</button>
</template>

<style>
p {
	color: blueviolet;
}
</style>