<script>
import Product from "./Product.svelte";
import Modal from "./Modal.svelte";
let products = [{
        id: "p1",
        title: "Book1",
        price: 2
    },
    {
        id: "p2",
        title: "Book2",
        price: 3
    }
]

function addToCart(event) {
    console.log(event);
}

function deleteProduct(event) {
    console.log(event.detail);
}
</script>

<style>
</style>

{#each products as product}

<Product
    {...product}
    on:add-to-cart={addToCart}
    on:delete={deleteProduct}
    />
    {/each}
    <Modal content="CONTENT">
        <h1 slot="header">Slot to use html inside Modal tag</h1>
        <h2>bye!</h2>
        <button slot="footer">Confirm</button>
    </Modal>
