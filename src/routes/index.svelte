<script context="module">
	export const prerender = true;
</script>

<script>
	import Headlines from '$lib/Headlines.svelte'
</script>

<svelte:head>
	<title>Home</title>
	<link rel="preconnect" href="https://fonts.googleapis.com">
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
	<link href="https://fonts.googleapis.com/css2?family=Merriweather:wght@300&display=swap" rel="stylesheet">
</svelte:head>

<main>
	<Headlines/>  
</main>


<style>
	main {
		text-align: center;
		padding-inline: 30vw;
		max-width: 240px;
		margin: 0 auto;
		background-color: rgb(237, 235, 235);
		font-family: 'Merriweather', serif;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}


</style>
