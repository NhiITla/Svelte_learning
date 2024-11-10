<script>
import Product from "./Product.svelte";
</script>

<style>
</style>

<Product productTitle="A Book" on:click="{()=>alert("CLICK")}"/>
