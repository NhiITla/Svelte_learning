<script>
    export let title; //export set data from our site
    export let sub;
    export let des;
    export let imageUrl;


</script>
<style>

</style>
<article>
    <header>
        <h1>{title}</h1>
        <h2>{sub}</h2>
        <h2>{des}</h2>
    </header>
    <div class="image">
        <img src="{imageUrl}" alt="{title}">
    </div>
    <div class="content">
        <p></p>
    </div>
    <footer>
        <button>SHOW DETAILS</button>
        <button>Favorite</button>
    </footer>
</article>