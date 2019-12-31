<script>
export let image;
export let title;
</script>
<div class="container">    
    <div class="card">
        <img src="{image}" alt="{title}">
        
        <div class="card-body">
            <h3>{title}</h3>

        </div>
    </div>
</div>

<style>
    .container {
        display: flex;
        flex-direction: row;
    }
    .card img{
        flex-grow: 1;
        height: 400px;
    }
</style>