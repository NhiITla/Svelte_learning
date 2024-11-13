<script>
import {
    createEventDispatcher,
    onDestroy,
    onMount,
    beforeUpdate,
    afterUpdate
} from 'svelte';

export let content;
const dispatch = createEventDispatcher();
let agreed = false;
let autoscroll = false;

onMount(() => {
    console.log("onMount");
});

onDestroy(() => {
    console.log("onDestroy");
});

beforeUpdate(() => {
    console.log("beforeUpdate");
    autoscroll = agreed;
});

afterUpdate(() => {
    console.log("afterUpdate");
    if(autoscroll){
        const modal = document.querySelector('.modal');
        modal.scrollTo(0, modal.scrollHeight)
    }
});

console.log("Script executed!")
</script>

<style>
.backdrop {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    background: rgba(0, 0, 0, 0.75);
    z-index: 10;
}

.modal {
    padding: 1rem;
    position: fixed;
    top: 10vh;
    left: 10%;
    width: 80%;
    max-height: 15vh;
    background: white;
    border-radius: 5px;
    z-index: 100;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    overflow: scroll;
}

header {
    border-bottom: 1px solid red;
}
</style>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<div class="backdrop" on:click="{()=> dispatch('cancel')}"/>

    <div class="modal">
        {@html content}
        <header>
            <slot name="header"/>
                </header>
                <div class="disclaimer">
                    <p>Before you leave, you need to agree to our terms!</p>
                    <button on:click="{()=>agreed=true}">Agree</button>
                </div>
                <slot/> <!--default slot-->
                    <footer>
                        <slot name="footer" didAgree={agreed}>
                            <button on:click="{()=>dispatch('close')}" disabled={!agreed}>close</button>
                        </slot>
                    </footer>
                    </div>
