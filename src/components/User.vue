<script>
export default {
	props: ['i', 'o', 'f'],
	data() {
		return {
			name: this.i
		}
	}
}
</script>

<template>
	<p>{{ name }}</p>
	<p>{{ o }}</p>
	<p>{{ f }}</p>
</template>
