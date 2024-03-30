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
</template>

<style>
p {
	color: blueviolet;
}
</style>