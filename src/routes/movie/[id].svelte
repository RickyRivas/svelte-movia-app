<script context="module">
	export async function load({ fetch, params }) {
		const key = '46c32cd440f713beae2fc73cedb32ee1';
		const id = params.id;
		const res = await fetch(
			`https://api.themoviedb.org/3/movie/${id}?api_key=${key}&language=en-US`
		);
		const movieDetail = await res.json();
		if (res.ok) {
			return {
				props: {
					// the variable of the data
					movieDetail
				}
			};
		}
	}
</script>

<script>
	export let movieDetail;
</script>

<div class="movie-details">
	<div class="img-container">
		<img
			src={'https://image.tmdb.org/t/p/original' + movieDetail.backdrop_path}
			alt={movieDetail.title}
		/>
	</div>
	<div class="txt-container">
		<h1>{movieDetail.title}</h1>
		<p class="overview">{movieDetail.overview}</p>
		<p>
			<span>Release Date:</span>{movieDetail.release_date}<br />
			<span>Budget:</span>{movieDetail.budget}<br />
			<span>Rating:</span>{movieDetail.vote_average}
			<span>Runtime:</span>
			{movieDetail.runtime}mins
		</p>
	</div>
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
		width: 100%;
		max-width: 500px;
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
</style>
