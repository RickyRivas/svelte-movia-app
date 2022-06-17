<script>
	import PopularMovies from './PopularMovies.svelte';
	// importing the data from the parent
	export let popular;
	// import movie card component
	import MovieCard from './MovieCard.svelte';
</script>

<h3>Popular Movies</h3>
<div class="popular-movies">
	<!-- Looping throught the popular array -->
	<!-- passing each movie object into the MovieCard component -->
	{#each popular as movie}
		<MovieCard {movie} />
	{/each}
</div>

<style>
	h3 {
		padding: 1em;
	}
	.popular-movies {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
		grid-gap: 1em;
	}
</style>
