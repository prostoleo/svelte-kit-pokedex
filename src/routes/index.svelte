<script context="module">
	export async function load({}) {
		const url = `https://pokeapi.co/api/v2/pokemon?limit=${150}`;

		const res = await fetch(url);
		const data = await res.json();

		const loadedPokemon = data.results.map((data, index) => {
			return {
				name: data.name,
				id: index + 1,
				image: `https://raw.githubusercontent.com/PokeApi/sprites/master/sprites/pokemon/${
					index + 1
				}.png`
			};
		});

		return {
			props: {
				pokemon: loadedPokemon
			}
		};
	}
</script>

<script>
	import uikit from 'uikit';
	import Card from '../components/Card.svelte';
	// import { pokemon } from '../stores/pokestore';

	// console.log('pokemon: ', $pokemon);
	export let pokemon;

	let searchText = '';
	let filteredPokemon = [];

	//* todo with store
	/* $: {
		if (!searchText) filteredPokemon = [...$pokemon];
		console.log('searchText: ', searchText);

		if (searchText.trim().length !== 0) {
			filteredPokemon = $pokemon.filter((pokeman) =>
				pokeman.name.toLowerCase().includes(searchText.toLowerCase())
			);
		}
	} */

	$: {
		if (!searchText) filteredPokemon = [...pokemon];
		console.log('searchText: ', searchText);

		if (searchText.trim().length !== 0) {
			filteredPokemon = pokemon.filter((pokeman) =>
				pokeman.name.toLowerCase().includes(searchText.toLowerCase())
			);
		}
	}
</script>

<svelte:head>
	<title>Svelte Kit Pokedex</title>
	<!-- <link href="../assets/uikit.css" rel="stylesheet" /> -->
</svelte:head>

<h1 class="text-3xl text-center font-bold my-6">Home page</h1>
<!-- <ul uk-accordion>
	<li class="uk-open">
		<a class="uk-accordion-title" href="#">Item 1</a>
		<div class="uk-accordion-content">
			<p>
				Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut
				labore et dolore magna aliqua.
			</p>
		</div>
	</li>
	<li>
		<a class="uk-accordion-title" href="#">Item 2</a>
		<div class="uk-accordion-content">
			<p>
				Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
				commodo consequat. Duis aute irure dolor reprehenderit.
			</p>
		</div>
	</li>
	<li>
		<a class="uk-accordion-title" href="#">Item 3</a>
		<div class="uk-accordion-content">
			<p>
				Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla
				pariatur. Excepteur sint occaecat cupidatat proident.
			</p>
		</div>
	</li>
</ul> -->
<input
	type="text"
	class="w-full rounded-md text-lg p-4 border-2"
	placeholder="Enter your search here.."
	bind:value={searchText}
/>
<div class="mt-4 grid grid-cols-2  gap-3 lg:grid-cols-3 xl:(grid-cols-4)">
	{#each filteredPokemon as pokeman}
		<Card {pokeman} />
	{/each}
</div>

<!-- <style>
	h1 {
		color: red;
	}
</style> -->
<style windi:preflights:global windi:safelist:global>
</style>
