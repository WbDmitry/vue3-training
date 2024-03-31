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
		}
	},
	methods: {
		getCurrentDate: function () {
			let currentDate = new Date();
			alert(currentDate)
		}
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
	{{ getCurrentDate() }}
	<button @click="getCurrentDate">Вывести дату</button>
</template>

<style>
p {
	color: blueviolet;
}
</style>