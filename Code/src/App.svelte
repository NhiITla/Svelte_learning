<script>
	export let name;
	import Header from "./UI/Header.svelte";
</script>

<style>
	h1 {
		color: purple;
	}
</style>

<Header/>
<h1>Hello 1 {name}!</h1>
