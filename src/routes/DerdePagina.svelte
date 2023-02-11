<script lang="ts">
	import video from '$lib/assets/video/woordenCollagePersoonlijkheid.mp4';

	import { onMount } from 'svelte';
	import { index } from '$lib/stores/indexStore';

	onMount(async () => {
		const myVideo = document.getElementById('myVideo') as HTMLVideoElement;
		const observer = new IntersectionObserver((entries) => {
			entries.forEach((entry) => {
				if (entry.isIntersecting) {
					myVideo.play();
					observer.unobserve(entry.target);
				}
			});
		});

		observer.observe(myVideo);
	});
</script>

<div class="derde-pagina-grid-container">
	<div class="titel">
		<h1>Persoonlijkheid</h1>
	</div>
	<div class="woordencollage">
		<video src={video} autoplay muted id="myVideo">
			<track kind="captions" />
		</video>
	</div>

	<a href="#pagina4" class="pijlRechts">
		<i class="fa-solid fa-chevron-right" />
	</a>

	<a href="#pagina2" class="pijlLinks">
		<i class="fa-solid fa-chevron-left" />
	</a>
</div>

<style>
	/* Derde pagina */
	h1 {
		/* juiste font ipv proxima nova */
		font-family: 'Philosopher', sans-serif;
		-webkit-text-fill-color: transparent;
		background: linear-gradient(190deg, rgba(255, 255, 255, 0) 0%, rgba(255, 255, 255, 1) 100%);
		background-clip: text;
		height: 100%;
	}

	@media only screen and (max-width: 680px) {
		h1 {
			font-size: 2.5rem;
			text-align: center;
			/* tekst iets helderder  */
			-webkit-text-fill-color: transparent;
			background: linear-gradient(
				190deg,
				rgba(255, 255, 255, 0.5) 30%,
				rgba(255, 255, 255, 1) 100%
			);
			background-clip: text;
		}
	}

	video {
		max-width: 100%;
		max-height: 100%;
		object-fit: cover;
		border-radius: 4em;
	}

	.derde-pagina-grid-container {
		width: 100%;
		height: 100%;
		display: grid;
		grid-template-columns: 0.1fr minmax(0, 1.3fr) 0.1fr;
		grid-template-rows: 0.3fr 0.6fr minmax(0, 2.8fr) 0.3fr;
		grid-auto-columns: 1fr;
		gap: 0px 0em;
		grid-auto-flow: row;
		grid-template-areas:
			'. . .'
			'. titel .'
			'. woordencollage .'
			'. . .';

		position: relative;
	}

	.pijlRechts {
		/* grid-area: pijlRechts;
		opacity: 0.5;
		font-size: 3rem;
		align-self: center;
		justify-self: center; */

		position: absolute;
		opacity: 0.5;
		font-size: 3rem;
		top: 50%;
		right: 2em;
	}
	.pijlLinks {
		/* grid-area: pijlLinks;
		opacity: 0.5;
		font-size: 3rem;
		align-self: center;
		justify-self: center; */
		position: absolute;
		opacity: 0.5;
		font-size: 3rem;
		top: 50%;
		left: 2em;
	}

	.woordencollage {
		justify-self: center;
		grid-area: woordencollage;
	}

	.titel {
		grid-area: titel;
		/* background-color: blue; */
		/* justify-self: center; */
	}
</style>
