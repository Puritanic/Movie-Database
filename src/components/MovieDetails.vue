<template>
	<div class="movie-wrapper" :style="styles">
		<div class="movie-info">
			<h1>{{ movie.title }}</h1>
			<h3>Release date: {{ movie.release_date }}</h3>
			<p>{{ movie.overview }}</p>
		</div>
	</div>
</template>

<script>
const BACKDROP_PATH = 'http://image.tmdb.org/t/p/w1280/';

export default {
	data() {
		return {
			movie: {}
		}
	},
	created() {
		this.fetchData();
	},
	computed: {
		// attach to CSS
		styles() {
			return {
				background: `center / cover no-repeat url(${BACKDROP_PATH}${this.movie.backdrop_path})`
			}
		}
	},
	methods: {
		async fetchData() {
			try {
				const res = await fetch(`https://api.themoviedb.org/3/movie/${this.$route.params.id}?api_key=${process.env.VUE_APP_MDB_KEY}`);
				this.movie = await res.json();

			} catch (err) {
				throw new Error(err);
			}
		}
	}

}
</script>

<style scoped>
.movie-wrapper {
	position: relative;
	padding-top: 50vh;
	background-size: cover;
	background-position: center center;
}
.movie-info {
	background: rgba(255, 255, 255, 0.7);
	color: #222;
	padding: 2rem 10%;
}
</style>
