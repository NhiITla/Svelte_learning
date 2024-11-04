<script>
import MeetupsItem from "./MeetupsItem.svelte";
export let meetups; //export to use in another component
</script>

<style>
section {
    width: 100%;
    display: grid;
    grid-template-columns: 1fr;
    grid-gap: 1rem;
}

@media (min-width: 768px) {
    section {
        grid-template-columns: repeat(2, 1fr);
    }
}
</style>

<section id="meetups">
    {#each meetups as meetup }
    <MeetupsItem
        title={meetup.title}
        sub={meetup.sub}
        des={meetup.des}
        imageUrl={meetup.imageUrl}/>

        {/each}

        </section>
