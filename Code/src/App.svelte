<script>
	import Header from "./UI/Header.svelte";
	import MeetupsItem from "./Meetups/MeetupsItem.svelte";

	const meetups=[
		{
			id:"m1",
			title:"Coding Bootcamp",
			sub:"Coding Bootcamp",
			des:"in this meetup, we will have some others thing",
			imageUrl:"https://kidlingoo.com/wp-content/uploads/flowers_name_in_english-980x510.jpg.webp",
			email:"email1@gmail.com"
		},
		{
			id:"m2",
			title:"Coding Bootcamp",
			sub:"Coding Bootcamp",
			des:"in this meetup, we will have some others thing",
			imageUrl:"https://dictionary.cambridge.org/images/thumb/flower_noun_002_14403.jpg?version=6.0.36",
			email:"email2@gmail.com"
		}

	]
</script>

<style>
</style>

<Header/>
{#each meetups as meetup }
	<MeetupsItem 
	title={meetup.title} 
	sub={meetup.sub} 
	des={meetup.des} 
	imageUrl={meetup.imageUrl}/>
	
{/each}
