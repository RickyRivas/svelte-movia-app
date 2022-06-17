<script>
	import { goto } from '$app/navigation';
	let inputValue = '';
	let active = false;
	function toggle() {
		active = !active;
	}
	function inActive() {
		if (inputValue) {
			active = true;
		} else {
			active = false;
		}
	}
	function submitSearch() {
		goto('/search/' + inputValue);
	}
</script>

<form class="search" on:submit|preventDefault={submitSearch}>
	<!-- displaying based on active status-->
	{#if !active}
		<label for="search-movie">Search Movie</label>
	{/if}

	<input
		on:blur={inActive}
		on:focus={toggle}
		bind:value={inputValue}
		name="search-movie"
		type="text"
		class={active ? 'selected' : ''}
	/>
	{#if inputValue}
		<button>Search</button>
	{/if}
</form>
<h1>{inputValue}</h1>

<style>
	button {
		font-size: 1em;
		width: 100px;
		height: 40px;
		color: white;
		background-color: black;
	}
	input {
		width: 100%;
	}
</style>
