<template>
	<li>
		<router-link :to="moviePath">
			<img :src="posterImg" :alt="movie.title">
		</router-link>
	</li>
</template>

<script>
const POSTER_PATH = 'http://image.tmdb.org/t/p/w154/';

export default {
	name: 'Movie',
	props: {
		movie: Object
	},
	computed: {
		posterImg() {
			return `${POSTER_PATH}${this.movie.poster_path}`;
		},
		moviePath() {
			return `/movie/${this.movie.id}`;
		}
	}
}
</script>

<style scoped>
img {
	box-shadow: 0 0 35px black;
}
</style>
