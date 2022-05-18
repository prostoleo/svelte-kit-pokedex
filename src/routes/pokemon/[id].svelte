<script context="module">
	export async function load({ params }) {
		const id = params.id;

		const url = `https://pokeapi.co/api/v2/pokemon/${id}`;

		const res = await fetch(url);

		const pokeman = await res.json();

		return {
			props: {
				pokeman
			}
		};
	}
</script>

<script>
	export let pokeman;
	console.log('pokeman: ', pokeman);
	const type = pokeman.types[0].type.name;
</script>

<h1 class="text-3xl text-center font-bold my-2 capitalize">{pokeman.name}</h1>
<div class="flex flex-col items-center mx-auto">
	<p>
		Type: <strong>{type}</strong> | Height: <strong>{pokeman.height}</strong> | Weight:
		<strong>{pokeman.weight}</strong>
	</p>
	<img src={pokeman.sprites['front_default']} alt={pokeman.name} class="w-64" />
</div>

<style windi:preflights:global windi:safelist:global>
</style>
