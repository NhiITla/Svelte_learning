<script>
	export let name;
	import Header from "./UI/Header.svelte";
	import MeetupsItem from "./Meetups/MeetupsItem.svelte";

	const meetups=[
		{
			id:"m1",
			title:"Coding Bootcamp",
			sub:"Coding Bootcamp",
			des:"in this meetup, we will have some others thing",
			imageUrl:"https://store.google.com/regionpicker?hl=en-US",
			email:"email1@gmail.com"
		},
		{
			id:"m2",
			title:"Coding Bootcamp",
			sub:"Coding Bootcamp",
			des:"in this meetup, we will have some others thing",
			imageUrl:"https://store.google.com/regionpicker?hl=en-US",
			email:"email2@gmail.com"
		}

	]
</script>

<style>
</style>

<Header/>
{#each meetups as meetup }
	<MeetupsItem/>
	
{/each}
