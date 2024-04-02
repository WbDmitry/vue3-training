<script>
import User from './components/User.vue'

export default {
	name: 'App',
	components: {
		User
	},

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
			products2: [
				{
					id: 1,
					name: 'product1',
				},
				{
					id: 2,
					name: 'product2',
				},
				{
					id: 3,
					name: 'product3',
				},
			],
			styles: {
				colorText: false,
			},
			isValid: true,
			isDisabled: false,
			messageInput: 'hello',
			numberInput: 5,
			isChecked: true,
			arrCheckbox: [],
			choice3: '',
			selected: '',
			isDisabled: false,
			isClickEnter: false,
			isClickLinkCtrl: false,
			users: [
				{
					id: 1,
					name: 'name1',
					surn: 'surn1',
					isEdit: false,
				},
				{
					id: 2,
					name: 'name2',
					surn: 'surn2',
					isEdit: false,
				},
				{
					id: 3,
					name: 'name3',
					surn: 'surn3',
					isEdit: false,
				},
			],
			items3: ['a', 'b', 'c', 'd', 'e'],
			users2: [
				{
					id: 1,
					name: 'name1',
					surn: 'surn1',
					isEdit: true,
				},
				{
					id: 2,
					name: 'name2',
					surn: 'surn2',
					isEdit: true,
				},
				{
					id: 3,
					name: 'name3',
					surn: 'surn3',
					isEdit: true,
				},
			]
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

		setColorText: function () {
			this.styles.colorText = !this.styles.colorText
		},

		setDisabled: function () {
			this.isDisabled = !this.isDisabled
		},

		clickEnter: function () {
			this.isClickEnter = true
		},

		clickLinkCtrl: function () {
			this.isClickLinkCtrl = true
		},

		deleteUser: function (id) {
			this.users = this.users.filter(user => {
				return user.id !== id
			})
		},
		deleteItems: function (index) {
			this.items3.splice(index, 1)
		},

		editUser: function (user) {
			user.isEdit = false
		},

		saveUser: function (user) {
			user.isEdit = true
		},

		editUser2: function (user) {
			user.isEdit = true
		},

		saveUser2: function (user) {
			user.isEdit = false
		}
	}
}
</script>

<template>
	<User i="Имя" o="Отчество" f="Фамилия" />
	<p>VisibleGroup: {{ visibleGroup }}</p>
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
		<!-- {{ getCurrentDate() }}  -->
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
		</div>
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

		<div v-for="items in items2">
			<p v-if="items > 0"> {{ items }}</p>
		</div>

		<ul>
			<li v-for="items in products2" :key="items.id">
				{{ items.id }}
				{{ items.name }}
			</li>
		</ul>


		<p :class="styles">Что такое Lorem Ipsum?</p>
		<button @click="setColorText">Управление классом</button>
		<p :class="{ active: true, valid: false }">Инлайн объект с КСС классами</p>
		<p :class="{ active: isValid, valid: isDisabled }">Классы через data</p>

		<input v-model="messageInput">
		<p> {{ messageInput }}</p>
		<p> {{ messageInput.toUpperCase() }}</p>
		<input type="number" v-model="numberInput">
		<p> {{ numberInput ** 2 }}</p>

		<input type="checkbox" v-model="isChecked">
		<p v-if="isChecked">Чекбокс: Активен</p>

		<input type="checkbox" v-model="arrCheckbox" value="Русский">Русский</input>
		<input type="checkbox" v-model="arrCheckbox" value="Английский">Английский</input>
		<input type="checkbox" v-model="arrCheckbox" value="Китайский">Китайский</input>
		<ul>
			<li v-for="element in arrCheckbox">{{ element }}</li>
		</ul>

		<input name="radio" type="radio" v-model="choice3" value="ru">Русский</input>
		<input name="radio" type="radio" v-model="choice3" value="en">Английский</input>
		<input name="radio" type="radio" v-model="choice3" value="ch">Китайский</input>
		<p v-if="choice3 == 'ru'">Cообщение на русском</p>
		<p v-else-if="choice3 === 'en'">The message is in English</p>
		<p v-else="choice3 === 'ch'">留言是中文的</p>

		<select v-model="selected">
			<option>value1</option>
			<option>value2</option>
			<option>value3</option>
		</select>

		<p>{{ selected }}</p>

		<select v-model="selected" :disabled="isDisabled">
			<option>value1</option>
			<option>value2</option>
			<option>value3</option>
		</select>
		<button @click="setDisabled">Блокировать селект</button>

		<input type="text" @keypress.enter="clickEnter">
		<p v-if="isClickEnter">Нажили Ентер</p>

		<a href="" @click.ctrl.exact="clickLinkCtrl">Ссылка</a>
		<p v-if="isClickLinkCtrl">Нажили Ctrl+Click на ссылку</p>

		<ul>
			<li v-for="user in users" :key="user.id">
				<template v-if="!user.isEdit">
					{{ user.name }}
					{{ user.surn }}
					<button @click="editUser2(user)">Редактировать</button>
					<button @click="deleteUser(user.id)">x</button>
				</template>
				<template v-else>
					<input type="text" v-model="user.name">
					<input type="text" v-model="user.surn">
					<button @click="saveUser2(user)">Сохранить</button>
				</template>
			</li>
		</ul>

		<ul>
			<li v-for="(items, index) in items3" :key="index">
				{{ items }}
				<button @click="deleteItems(index)">x</button>
			</li>
		</ul>

		<ul>
			<li v-for="user in users2" :key="user.id">
				<template v-if="user.isEdit">
					{{ user.name }}
					{{ user.surn }}
					<button @click="editUser(user)">
						Редактировать
					</button>
				</template>
				<template v-else>
					<input type="text" v-model="user.name">
					<input type="text" v-model="user.surn">
					<button @click="saveUser(user)">Сохранить</button>
				</template>
			</li>
		</ul>
	</div>

</template>

<style>
.colorText {
	color: blueviolet;
	text-decoration: line-through;
}
</style>