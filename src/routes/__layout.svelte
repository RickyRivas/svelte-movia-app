<!-- __layout is the file that creates the layout of every page. -->
<script>
	// good to put global css in this file because it will be applied to every page
	import global from '../global.css';
	import nav from '../components/nav.svelte';
	import Nav from '../components/nav.svelte';
</script>

<svelte:head>
	<title>Ricky's Movie App</title>
</svelte:head>

<Nav />
<slot />
<footer>footer</footer>
