<script>
export default {
	name: 'App',
	data() {
		return {
			firstName: 'Dmitry',
			lastName: 'Wb',
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
</template>

<style>
p {
	color: blueviolet;
}
</style>