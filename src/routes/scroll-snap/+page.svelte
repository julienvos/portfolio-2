<script lang="ts">
	// import type { PageData } from './$types';

	// export let data: PageData;
</script>

<div class="scroll-container">
	<section>
		<h1>Page 1</h1>
	</section>
	<section>
		<h1>Page 2</h1>
	</section>
	<section>
		<h1>Page 3</h1>
	</section>
</div>

<style>
	/* om de y scrollbar weg te krijgen >> overflow-y in de body */
	:global(body) {
		overflow-y: hidden;
	}

	.scroll-container {
		display: flex;
		scroll-snap-type: x mandatory;
		/* om de snapping scroll te krijgen -->> overflow-x (of y) op scroll */
		overflow-x: hidden;
	}

	section {
		scroll-snap-align: start;
		flex: none;
		width: 100vw;
		height: 100vh;

		/* om de horizontal scroll bar weg te halen  >>>> maxh-width:100% */

		max-height: 100%;

		display: flex;
		justify-content: center;
		align-items: center;
		scroll-snap-align: start;
	}
	.scroll-container section:nth-child(1) {
		background-color: green;
		color: black;
	}

	.scroll-container section:nth-child(2) {
		background-color: purple;
		color: red;
	}

	.scroll-container section:nth-child(3) {
		background-color: blueviolet;
		color: yellow;
	}
</style>
