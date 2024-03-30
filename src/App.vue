<script>
export default {
	name: 'App',
	data() {
		return {
			firstName: 'Dmitry',
			lastName: 'Wb',
			linkText: 'Yandex поиск',
			href: 'https://ya.ru'
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
</template>

<style>
p {
	color: blueviolet;
}
</style>