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
			arr2: ['x', 'y', 'z'],
			arr3: ['a', 'c', 'b',],
			obj: { x: 1, y: 2, z: 3 },
			textParagraph: 'Что такое Lorem Ipsum?',
			cost: 2000,
			amount: 1,
			visible: true,
			isAdmin: false,
			day: 1,
			age: 25,
			visibleGroup: false,
			items: [1, 2, 3],
			items2: [1, -2, 3, -4, 5],
			obj2: {
				user1: '100$', user2: '200$', user3: '300$',
			},
			hrefs: [
				{ href: '1.html', text: 'text1' },
				{ href: '2.html', text: 'text2' },
				{ href: '3.html', text: 'text3' },
			],
			products: [
				{
					name: 'product1',
					price: 100,
					quantity: 5
				},
				{
					name: 'product2',
					price: 200,
					quantity: 4
				},
				{
					name: 'product3',
					price: 300,
					quantity: 3
				},
			],

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

		setAdmin: function () {
			this.isAdmin = !this.isAdmin
		},

		setDays: function (params) {
			this.day = params
		},

		setAge: function (params) {
			this.age = params
		},

		setVisibleGroup: function () {
			this.visibleGroup = !this.visibleGroup
		},

		addArr: function () {
			this.arr3.push('d');
		},

		deleteFirst: function () {
			this.arr3.shift();
		},

		deleteLast: function () {
			this.arr3.pop();
		},

		deletePenultimate: function () {
			this.arr3.splice(-2, 1);
		},

		sortArr: function () {
			this.arr3.sort();
		},

		reverseArr: function () {
			this.arr3.reverse();
		},
	}
}
</script>

<template>
	<!-- <p>VisibleGroup: {{ visibleGroup }}</p>
	<button @click="setVisibleGroup()">{{ visibleGroup ? 'Скрыть' : 'Показать' }}</button>
	<div v-show="visibleGroup">
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
		 {{ getCurrentDate() }} 
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

		<p v-if="isAdmin">isAdmin: true</p>
		<p v-else>isAdmin: false</p>
		<button @click="setAdmin()">isAdmin</button>

		<p v-if="day === 1">1 = Понедельник</p>
		<p v-if="day === 2">2 = Вторник</p>
		<p v-if="day === 3">3 = Среда</p>
		<p v-if="day === 4">4 = Четверг</p>
		<p v-if="day === 5">5 = Пятница</p>
		<p v-if="day === 6">6 = Суббота</p>
		<p v-if="day === 7">7 = Воскресенье</p>
		<button @click="setDays(1)">1</button>
		<button @click="setDays(2)">2</button>
		<button @click="setDays(3)">3</button>
		<button @click="setDays(4)">4</button>
		<button @click="setDays(5)">5</button>
		<button @click="setDays(6)">6</button>
		<button @click="setDays(7)">7</button>

		<p v-if="age <= 18">подросток</p>
		<p v-else-if="age >= 19 && age <= 25">молодой человек</p>
		<p v-if="age > 26">мужчина</p>
		<button @click="setAge(16)">16</button>
		<button @click="setAge(21)">21</button>
		<button @click="setAge(25)">25</button>
		<button @click="setAge(30)">30</button>
	</div>

	<div v-for="items in arr">{{ items }}</div>
	<div v-for="items in arr">{{ items ** 2 }}</div>
	<ul>
		<li v-for="items in arr">{{ items }}</li>
	</ul>

	<ul>
		<li v-for="(items, key) in arr2"> {{ key + 1 }} - {{ items }}</li>
	</ul>

	<ul>
		<li v-for="(items, key, index) in obj2">{{ key }} - {{ items }} - {{ index + 1 }}</li>
	</ul>

	<div v-for="items in items">
		<p>{{ items }}</p>
		<p class="divider"></p>
	</div>

	<ul>
		<template v-for="items in items">
			<li>{{ items }}</li>
			<li class="divider"></li>
		</template>
</ul>

<ul>
	<li v-for="item in hrefs">
		<a :href="item.href">{{ item.text }}</a>
	</li>
</ul>

<table>
	<tr v-for="items in products">
		<td>{{ items.name }}</td>
		<td>{{ items.price }}</td>
		<td>{{ items.quantity }}</td>
	</tr>
</table>

<p v-for="num in 30">{{ num }}</p>

<div v-for="items in items2">
	<p v-if="items > 0"> {{ items }}</p>
</div> -->
	<button @click="addArr">Добавить</button>
	<button @click="deleteFirst">Удалить первый пункт</button>
	<button @click="deleteLast">Удалить последний пункт</button>
	<button @click="deletePenultimate">Удалить предпоследний пункт</button>
	<button @click="sortArr">Сортировать</button>
	<button @click="reverseArr">В обратном порядке</button>
	<ul>
		<li v-for="elem in arr3">
			{{ elem }}
		</li>
	</ul>
</template>

<style>
p {
	color: blueviolet;
}
</style>