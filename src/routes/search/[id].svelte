<script context="module">
	import MovieCard from './../../components/MovieCard.svelte';
	export async function load({ fetch, params }) {
		const key = '46c32cd440f713beae2fc73cedb32ee1';
		const res = await fetch(
			`https://api.themoviedb.org/3/search/movie?api_key=${key}&language=en-US&query=${params.id}&page=1&include_adult='false'`
		);
		const data = await res.json();
		console.log(data);
		if (res.ok) {
			return {
				props: {
					searchedMovie: data.results
				}
			};
		}
	}
</script>

<script>
	export let searchedMovie;
</script>

<h1>Based on your search results:</h1>
<div class="movies">
	{#each searchedMovie as movie}
		<MovieCard {movie} />
	{/each}
</div>

<style>
	h1 {
		padding: 1rem 0rem 2rem;
	}
	p {
		padding: 1rem 0rem;
	}
	.img-container {
		width: 100%;
	}
	img {
		object-fit: cover;
		width: 100%;
		border-radius: 1em;
	}
	.movie-details {
		margin: 2em 20%;
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
		text-align: center;
	}
	span {
		font-weight: bold;
	}
	.movies {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
		grid-gap: 1em;
		justify-content: center;
		align-items: flex-start;
	}
</style>
