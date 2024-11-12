<script>
export let productTitle;
import {
    createEventDispatcher
} from 'svelte';
const dispatch = createEventDispatcher();
function addToCart(){
    dispatch('add-to-cart',{id:"p1"});
}
</script>

<article>
    <h1>{productTitle}</h1>
    <button on:click="{addToCart}">Add to Cart because on:click so event will handle on App component</button>
    <button on:click="{()=> dispatch('delete','p1')}">Delete</button>
</article>
