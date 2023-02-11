<script lang="ts">
	import VierdePagina from './VierdePagina.svelte';

	import DerdePagina from './DerdePagina.svelte';

	import TweedePagina from './TweedePagina.svelte';

	import EerstePagina from './EerstePagina.svelte';
	import { onMount } from 'svelte';

	onMount(() => {
		// verwijder hash van string
		let hash = window.location.hash.substring(1);
		console.log(hash);
		if (hash) {
			// scroll naar pagina
			document.getElementById(hash)?.scrollIntoView();
			// je zou ook iets kunnen doen als Preserve scroll
			// https://natclark.com/tutorials/svelte-maintain-scroll-position/
		}
	});
</script>

<div class="scroll-container">
	<section id="pagina1">
		<EerstePagina />
	</section>

	<section id="pagina2">
		<TweedePagina />
	</section>
	<section id="pagina3">
		<DerdePagina />
	</section>

	<section id="pagina4">
		<VierdePagina />
	</section>
</div>

<style>
	/* "global settings" */
	section {
		height: 100vh;
		width: 100vw;
		/* voorkomt dat alle paginas aan elkaar wordt geplakt */
		flex: none;
		scroll-snap-align: start;
	}

	.scroll-container {
		display: flex;
		/* horizontaal scrollen op mobile */
		/* overflow x in de container en overflow y in de body */
		overflow-x: scroll;
		scroll-snap-type: x mandatory;
		scroll-behavior: smooth;
	}

	:global(body) {
		overflow-y: hidden;
		scroll-behavior: smooth;
	}
</style>
