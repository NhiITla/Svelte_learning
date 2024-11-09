<script>
import Button from "../UI/Button.svelte";
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
        <Button href="mailto:{sub}" caption="Contact"/>
            <Button type="button" caption="Show details"/>
                <Button mode="outline" type="button" caption="Favorite"/>
                    </footer>
                    </article>
