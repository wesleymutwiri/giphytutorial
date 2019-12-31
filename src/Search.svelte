<script>
    import Post from './Post.svelte';
    const API_KEY = "jPTD1RPz6kvtZPX41YGy3sBmSJfj6nu3";
    let search = "";
    let posts;

    function handleSubmit(e){
        e.preventDefault();
        fetch(`https://api.giphy.com/v1/gifs/search?api_key=${API_KEY}&q=${search}&limit=25&offset=0&rating=G&lang=en`)
        .then(resp => resp.json())
        .then(data => (posts=data));
        console.log(posts.data);
    }
</script>
<div>
    <h2>
        Search for GIFs
    </h2>
    <form on:submit={handleSubmit}>
        <input type="text" bind:value={search}>
        <button>Search</button>
    </form>
    {#if posts}
        {#each posts as post}
        <Post image={post.images.original.url} title={post.title}/>
        {/each}
    {/if}
</div>