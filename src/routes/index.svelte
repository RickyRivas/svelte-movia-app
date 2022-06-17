<!-- Use script context module for server side rendering -->
<script context="module">
	const key = '46c32cd440f713beae2fc73cedb32ee1';
	// below function is same as an onMount function
	// triggers when the component loads
	export async function load({ fetch }) {
		// fetch data from movie database
		const res = await fetch(
			`https://api.themoviedb.org/3/movie/popular?api_key=${key}&language=en-US&page=1`
		);

		let data = await res.json();

		if (res.ok) {
			// returning props allows the app to use the data being returned from this function
			return {
				props: {
					popular: data.results
				}
			};
		}
	}
</script>

<script>
	// importing a component
	import PopularMovies from '../components/PopularMovies.svelte';
	import SearchMovie from '../components/SearchMovie.svelte';
	// accessing the popular property from the props object
	export let popular;
</script>

<section>
	<SearchMovie />
	<!-- passing data from parent to child -->
	<!-- create attribute with any name and set it to a var from this component-->
	<!-- this data will be accessible by the attribute name. 'movies' in this case -->
	<!-- if attribute name and var name is the same use {name}-->
	<!-- <PopularMovies popular={popular} /> -->
	<PopularMovies {popular} />
</section>
