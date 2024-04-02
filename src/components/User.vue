<script>
export default {
	props: {
		arr: Array,
	},

	data() {
		return {
			name: ''
		}
	}
}
</script>

<template>
	<ul>
		<li v-for="item in arr">{{ item }}</li>
	</ul>
</template>
