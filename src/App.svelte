<script>
	import { onMount } from "svelte";
  import Card from "./components/Card.svelte";
	import Header from './components/Header.svelte';
	import Main from './components/Main.svelte';
	import Sidebar from './components/Sidebar.svelte';
	import TimeLine from './components/TimeLine.svelte';



const API = "https://rickandmortyapi.com/api/character";
let data = [];
let characters = [];


onMount(async () => {
	const response = await fetch(API)
	data = await response.json();
	characters = data.results;
});

</script>



<style>

	:global(body){
		background-color: #fafafa;
		color:rgba(38,38,38, 07);
		font-family: "Lato", sans-serif;
		margin: 0; 
		padding: 0;
		font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, "Noto Sans", sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";
    box-sizing: inherit;
}


	:global(h1, h2, h3) {
		margin: 0;
		padding: 0;
	}
</style>



<Header/>
<Main>
		<TimeLine characters={data.results} />
		<Sidebar  />
</Main>
