<script lang="ts">
</script>

<div class="grid-container">
	<div class="titel">
		<h1><slot name="titel" /></h1>
	</div>

	<div class="tekst">
		<slot name="tekst">plaats hier de tekst</slot>
	</div>

	<div class="app">
		<slot name="app">plaats hier de foto</slot>
	</div>
</div>

<style>
	h1 {
		/* juiste font ipv proxima nova */
		font-family: 'Philosopher', sans-serif;
		-webkit-text-fill-color: transparent;
		background: linear-gradient(190deg, rgba(255, 255, 255, 0) 0%, rgba(255, 255, 255, 1) 100%);
		background-clip: text;
		/* om geen clipping te krijgen */
		height: 100%;
		font-size: 4rem;
	}

	.grid-container {
		height: 100vh;
		display: grid;
		grid-template-columns: 0.3fr minmax(0, 1.4fr) minmax(0, 2fr) 0.3fr;
		grid-template-rows: 0.3fr 0.5fr minmax(0, 2.9fr);
		grid-auto-columns: 1fr;
		gap: 2em 0em;
		grid-auto-flow: row;
		grid-template-areas:
			'. . . .'
			'. titel titel .'
			'. tekst app .';
	}

	.titel {
		grid-area: titel;
	}

	.tekst {
		grid-area: tekst;
		text-align: center;
	}

	.app {
		grid-area: app;
	}

	@media (max-width: 800px) {
		.grid-container {
			display: flex;
			flex-direction: column;
			flex-wrap: nowrap;
			justify-content: flex-start;
			align-items: stretch;
			align-content: normal;
			margin: 1em;
		}

		.titel {
			display: block;
			flex-grow: 0.5;
			flex-shrink: 1;
			flex-basis: 0px;
			align-self: auto;
			order: 1;
		}

		.app {
			display: block;
			flex-grow: 1;
			flex-shrink: 1;
			flex-basis: 0px;
			align-self: auto;
			order: 2;
		}

		.tekst {
			display: block;
			flex-grow: 1.5;
			flex-shrink: 1;
			flex-basis: 0px;
			align-self: auto;
			order: 3;
		}
	}
</style>
