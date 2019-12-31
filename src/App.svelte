<script>
	import { onMount } from "svelte";
	import Post from './Post.svelte';
	import Search from './Search.svelte';
	const API_KEY = "jPTD1RPz6kvtZPX41YGy3sBmSJfj6nu3";
	const TRENDING_URL = `https://api.giphy.com/v1/gifs/trending?api_key=${API_KEY}&limit=25&rating=G`;
	
	let posts = [];

	onMount(async function() {
		let calling = await fetch(TRENDING_URL);
		let p = await calling.json();
		posts = p["data"];
	});
</script>

<main>
	<Search/>
	<div class="container">
	{#each posts as post}
		<Post image={post.images.original.url} title={post.title}/>
	{/each}
	</div>
</main>

