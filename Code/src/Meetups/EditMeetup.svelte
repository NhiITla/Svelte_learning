<script>
import TextInput from "../UI/TextInput.svelte";
import Button from "../UI/Button.svelte";
import {
    createEventDispatcher
} from 'svelte';

let title = '';
let sub = '';
let des = '';
let imageUrl = '';

const dispatch = createEventDispatcher();

function submitForm() {
    dispatch('save', {
        title: title,
        sub: sub,
        imageUrl: imageUrl
    })
}
</script>

<style>
form {
    width: 30rem;
    max-width: 90%;
    margin: auto;
}
</style>

<form on:submit|preventDefault={submitForm}>
    <TextInput
        id="title"
        label="Title"
        type = "Text"
        value={title}
        on:input={event =>(title = event.target.value)} />
    <TextInput
        id="sub"
        label="Sub"
        type = "Text"
        value={sub}
        on:input={event =>(sub = event.target.value)} />
    <TextInput
        id="imageUrl"
        label="Image Url"
        type = "Text"
        value={imageUrl}
        on:input={event =>(imageUrl = event.target.value)} />
    <TextInput
        id="des"
        label="Description"
        controlType = "textarea"
        value={des}
        on:input={event =>(des = event.target.value)} />

    <Button type="submit" caption="Save"/>
        </form>
