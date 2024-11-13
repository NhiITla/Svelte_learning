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

let showModal = false;
let closeable=false;
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

    <button on:click="{()=>showModal=true}">Show Modal</button>
    {#if showModal}
    <Modal content="CONTENT"
        on:cancel={()=>(showModal=false)}
        on:close ={()=>showModal=false}
        let:didAgree={closeable} 
        >
        <!--Use let and didAgree to pass through the data-->
        <h1 slot="header">Slot to use html inside Modal tag</h1>
        <h2>bye!</h2>
        <button slot="footer" on:click={()=>showModal=false} disabled={!closeable}>Confirm</button>
    </Modal>
    {/if}
