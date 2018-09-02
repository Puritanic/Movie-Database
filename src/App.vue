<template>
	<div id="app">
		<div class="app">
			<Header :title="title" />
			<router-view />
		</div>
	</div>
</template>

<script>
import Header from './components/Header.vue'

console.log(process.env)

export default {
	name: 'app',
	data() {
		return {
			title: 'Vue Movie DB',
		}
	},
	components: {
		Header
	}
}
</script>

<style>
#app {
	font-family: 'Avenir', Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: aliceblue;
	height: 100%;
}
.app {
	height: 100%;
}
</style>
