<script lang="ts">
	import EerstePagina from './EerstePagina.svelte';
	import video from '$lib/assets/video/Persoonlijkheid.mp4';
</script>

<div class="scroll-container">
	<EerstePagina />

	<!-- <section>
		<div class="tweede-pagina__grid-container">
			<div class="tweede-pagina__titel">
				<h1 class="tracking-in-contract">Wie ben ik?</h1>
			</div>

			<div class="tweede-pagina__tekst">
				<ul class="introductie">
					<li>27 Jaar</li>
					<li>Zwartsluis, Overijssel</li>
					<li>Voormalig IT Trainee YoungCapital NEXT</li>
					<li>Afgestudeerd Bewegingswetenschapper</li>
					<li>Master Specialisatie Sport</li>
					<li>Interesse Techniek & Gezondheid</li>
				</ul>
			</div>
		</div>
	</section> -->
	<!-- <section>
		<div class="derde-pagina__grid-container">
			<div class="pagina-titel" />
			<div class="woorden-collage">
				<video src={video} autoplay muted>
					<track kind="captions" />
				</video>
			</div>
		</div>
	</section> -->
</div>

<style>
	li {
		font-family: 'Merriweather', serif;
		margin: 20px 0;
	}

	ul li {
		overflow: hidden;
		white-space: nowrap;
		width: 0;
		animation: typing 2s steps(30, end) 1s 1 normal forwards;
	}

	ul li:nth-child(1) {
		animation-delay: 1s;
	}
	ul li:nth-child(2) {
		animation-delay: 2s;
	}
	ul li:nth-child(3) {
		animation-delay: 3.5s;
	}
	ul li:nth-child(4) {
		animation-delay: 5s;
	}
	ul li:nth-child(5) {
		animation-delay: 7s;
	}
	ul li:nth-child(6) {
		animation-delay: 8s;
	}

	@keyframes typing {
		from {
			width: 0;
		}
		to {
			width: 100%;
		}
	}

	ul li {
		list-style: circle;
	}

	h1 {
		/* juiste font ipv proxima nova */
		font-family: 'Philosopher', sans-serif;
		-webkit-text-fill-color: transparent;
		background: linear-gradient(190deg, rgba(255, 255, 255, 0) 0%, rgba(255, 255, 255, 1) 100%);
		background-clip: text;
	}

	.tweede-pagina__grid-container {
		height: 100%;
		width: 100%;
		display: grid;
		grid-template-columns: 0.3fr repeat(2, 1.7fr) 0.3fr;
		grid-template-rows: 0.3fr 0.6fr 2.7fr 0.4fr;
		grid-auto-columns: 1fr;
		grid-auto-rows: 1fr;
		gap: 0px 0em;
		grid-auto-flow: row;
		grid-template-areas:
			'. . . .'
			'. Titel Titel .'
			'. Tekst . .'
			'. . . .';
	}

	.tweede-pagina__titel {
		background-color: blue;
		grid-area: Titel;
	}

	.tweede-pagina__tekst {
		display: grid;
		grid-template-columns: 0.4fr 2.2fr 0.4fr;
		grid-template-rows: 0.4fr repeat(2, 1.6fr) 0.4fr;
		gap: 0px 0px;
		grid-template-areas:
			'. . .'
			'. introductie .'
			'. introductie .'
			'. . .';
		grid-area: Tekst;
		background-color: green;
	}
	.introductie {
		background-color: purple;
		grid-area: introductie;
	}

	section {
		height: 100vh;
		width: 100vw;
		/* voorkomt dat alles aan elkaar wordt geplakt */
		flex: none;
	}

	.scroll-container {
		display: flex;
	}

	.tracking-in-contract {
		animation: tracking-in-contract 0.8s cubic-bezier(0.215, 0.61, 0.355, 1) forwards;
	}

	@keyframes fade-in-right {
		0% {
			transform: translateX(50px);
			opacity: 0;
		}
		100% {
			transform: translateX(0);
			opacity: 1;
		}
	}

	@keyframes tracking-in-contract {
		0% {
			letter-spacing: 1em;
			opacity: 0;
		}
		40% {
			opacity: 0.6;
		}
		100% {
			letter-spacing: normal;
			opacity: 1;
		}
	}

	/* Derde pagina */
	.derde-pagina__grid-container {
		width: 100%;
		height: 100%;
		display: grid;
		grid-template-columns: 0.5fr 1.9fr 0.6fr;
		grid-template-rows: 0.3fr minmax(0, 0.6fr) minmax(0, 2.7fr) 0.4fr;
		gap: 0px 0em;
		grid-template-areas:
			'. . .'
			'. pagina-titel .'
			'. woorden-collage .'
			'. . .';
	}

	.pagina-titel {
		grid-area: pagina-titel;
		background-color: blue;
	}

	.woorden-collage {
		grid-area: woorden-collage;
		background-color: green;
	}

	video {
		object-fit: cover;
		/* max-height en max-width zorgen voor de juiste grootte*/
		max-height: 100%;
		max-width: 100%;
	}
</style>
