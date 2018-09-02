<template>
	<header>
		<router-link to="/">
			<h1>{{ newTitle }}</h1>
		</router-link>
	</header>
</template>

<script>

export default {
	name: 'Header',
	props: {
		title: String
	},
	computed: {
		newTitle() {
			return this.title.toUpperCase();
		}
	}
}
</script>
 
<style scoped>
header {
	background-color: #111;
	padding: 20px;
	color: white;
}
h1 {
	margin: 0;
}
a {
	text-decoration: none;
	color: aliceblue;
}
</style>
