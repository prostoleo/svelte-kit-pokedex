<script>
	import { fade } from 'svelte/transition';
	export let pokeman;
</script>

<a
	href={`/pokemon/${pokeman.id}`}
	class="shadow shadow-md p-4 flex flex-col items-center hover:(shadow-lg)"
	transition:fade
>
	<img class="h-40 w-40 object-cover" src={pokeman.image} alt={pokeman.name} />
	<h2 class="text-xl font-semibold capitalize">{pokeman.name}</h2>
</a>
