<script>
export let title;
export let price;
export let bestseller = true;

import {
    createEventDispatcher
} from 'svelte';
const dispatch = createEventDispatcher();

function addToCart() {
    dispatch('add-to-cart', {
        id: "p1"
    });
}
</script>

<article>
    <h1>{title}</h1>
    <h1>${price}</h1>
    {#if bestseller}
    <h3>BEST SELLER</h3>
    {/if}
    <button on:click="{addToCart}">Add to Cart because on:click so event will handle on App component</button>
    <button on:click="{()=> dispatch('delete','p1')}">Delete</button>
</article>
