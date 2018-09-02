<template>
	<ul>
		<li v-for="movie in movies" :key="movie.id">
			<Movie :movie="movie" />
		</li>
	</ul>
</template>

<script>
import Movie from './Movie.vue';

export default {
	name: 'MoviesList',
	data() {
		return {
			movies: []
		}
	},
	components: {
		Movie
	},
	created() {
		this.fetchData();
	},
	methods: {
		async fetchData() {
			try {
				const res = await fetch(`https://api.themoviedb.org/3/discover/movie?sort_by=popularity.desc&api_key=${process.env.VUE_APP_MDB_KEY}`);
				const movies = await res.json();

				this.movies = movies.results;
			} catch (err) {
				throw new Error(err);
			}
		}
	}
}
</script>

<style scoped>
ul {
	display: grid;
	list-style: none;
	padding: 1rem;
	margin: 0;
	grid-row-gap: 1rem;
	grid-template-columns: repeat(6, 1fr);
}
</style>
