<script>
	// accessing the data being passed from the parent
	export let movie;
</script>

<div class="movie-card">
	<!-- dynamic routing by accessing the id-->
	<a href={'/movie/' + movie.id}>
		<img src={'https://image.tmdb.org/t/p/w500' + movie.poster_path} alt={movie.title} />
	</a>

	<div class="description">
		<h2>{movie.title}</h2>
		<p>{movie.release_date}</p>
	</div>
</div>

<!-- <h1>{movie.id}</h1> -->
<style>
	img {
		object-fit: cover;
		width: 100%;
		height: 30vw;
		border-radius: 1em;
	}
	h2 {
		margin: 0;
	}
</style>
