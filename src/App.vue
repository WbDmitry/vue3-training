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
		}
	}
}
</script>

<template>
	<p>Что такое Lorem Ipsum?</p>
	<div>
		{{ lastName }}
	</div>
	<div>
		{{ firstName }}
	</div>
	<div>
		<a v-bind:href="href" target="_blank">{{ linkText }}</a>
	</div>
	<div>
		<a :href="href" target="_blank">{{ linkText }}</a>
	</div>
	{{ num1 ** 2 }}
	{{ num1 + num2 }}
	<p>Вывод каждого числа: {{ arr[0] }},{{ arr[1] }}, {{ arr[2] }}</p>
	<p>Сумма чисел: {{ arr[0] + arr[1] + arr[2] }}</p>
</template>

<style>
p {
	color: blueviolet;
}
</style>