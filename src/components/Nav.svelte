<script>
	import Container from './Container.svelte';
</script>

<header class="p-3 bg-blue-800 text-light-50">
	<Container>
		<div class="wrapper flex justify-between">
			<div class="logo w-auto">
				<a href="/">Pokedex</a>
			</div>

			<nav>
				<ul class="flex gap-2 underline">
					<li><a href="/">Home</a></li>
					<li><a href="/about">About</a></li>
				</ul>
			</nav>
		</div>
	</Container>
</header>

<style lang="scss">
</style>
