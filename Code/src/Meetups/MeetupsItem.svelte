<script>
import Button from "../UI/Button.svelte";
import Badge from "../UI/Badge.svelte";
import {
    createEventDispatcher
} from 'svelte';
export let id;
export let title; //export set data from our site
export let sub;
export let des;
export let imageUrl;
export let isFav;

const dispatch = createEventDispatcher();
</script>

<style>

</style>

<article>
    <header>
        <h1>
            {title}
            {#if isFav}
            <Badge>FAVORITE</Badge>
            {/if}
        </h1>
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
        <Button href="mailto:{sub}">Contact</Button>
        <Button type="button">Show detail</Button>
        <Button
            mode="outline"
            color = {isFav? null :'success'}
            type="button"
            on:click={() => dispatch('toggle-favorite',id)}>
            {isFav ? 'UnFavorite':'Favorite'}</Button>
    </footer>
</article>
