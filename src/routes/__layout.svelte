<script>
	import Container from '../components/Container.svelte';
	import Nav from '../components/Nav.svelte';
</script>

<Nav />
<main>
	<Container>
		<slot />
	</Container>
</main>
