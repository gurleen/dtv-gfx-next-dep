<script lang="ts">
	import router from "page";
	import Demo from "./Demo.svelte";
	import Scorebug from "./scorebug/Scorebug.svelte";

	let page;

	router('/demo', () => page = Demo);
	router('/scorebug', () => page = Scorebug);
	router.start();
</script>

<main>
	<svelte:component this={page} />
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>