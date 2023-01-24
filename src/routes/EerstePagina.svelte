<script lang="ts">
	import MyButton from '$lib/components/MyButton.svelte';
	import video from '$lib/assets/video/smoke.mp4';
	import foto from '$lib/assets/images/portret-zwart-wit.jpeg';
</script>

<section>
	<div class="grid-container">
		<div class="naam">
			hoi
			<!-- <div class="voornaam">
				hoi
				<video src={video} autoplay muted width="600" height="200">
					<track kind="captions" />
				</video>
				<h1>
					<span>J</span><span>U</span><span>L</span><span>I</span><span>E</span><span>N</span>
				</h1>
			</div>
			<div class="achternaam">
				<video class="achternaam__video" src={video} autoplay muted width="600" height="200">
					<track kind="captions" />
				</video>
				<h1><span>V</span><span>O</span><span>S</span></h1>
				yo
			</div> -->
		</div>

		<div class="knoppen">
			<!-- <MyButton name="CV" />
			<MyButton name="Projecten" /> -->
			hoi
		</div>

		<div class="plaatje">
			<!-- <img src={foto} alt="portret foto" /> -->
			hallo
		</div>
	</div>
</section>

<style>
	.grid-container {
		height: 100%;
		width: 100%;
		display: grid;

		grid-template-columns: 0.3fr minmax(0, 1fr) minmax(0, 1fr) 0.3fr;
		grid-template-rows: 1fr 2fr 2fr 1fr;

		gap: 0px 2em;

		/* explicit grid */
		grid-template-areas:
			'. . . .'
			'. naam plaatje .'
			'. knoppen plaatje .'
			'. . . .';
	}

	@media only screen and (max-width: 1150px) {
		.grid-container {
			/* bij grids -->>  minmax(0, 1fr) AANBEVOLEN  */
			grid-template-columns: minmax(0, 1fr);
			grid-template-rows: 0.2fr minmax(0, 1fr) minmax(0, 1fr) 0.3fr;
			/* reset gap vanuit desktop */
			gap: 0em 0em;

			grid-template-areas:
				'.'
				'plaatje'
				'naam'
				'knoppen';
		}

		video {
			/* aspect-ratio: 6/1; */
			/* height: 100%;
			width: 100%; */
			opacity: 0.4;
		}

		.knoppen {
			/* justify-self: center; */
			background-color: blue;
		}
		.naam {
			/* justify-self: center; */
			background-color: bisque;
		}

		.plaatje {
			background-color: aqua;
		}

		.voornaam {
			justify-content: center;
			align-items: flex-start;
		}

		/* reset de translate */
		.achternaam__video {
			/* transform: translate(0, 0); */
		}

		.achternaam {
			/* justify-content: center;
			align-items: flex-start; */
		}
	}

	img {
		width: 100%;
		height: 100%;
		object-fit: cover;
	}
	video {
		object-fit: cover;
		max-height: 100%;
		max-width: 100%;
		/* aspect ratio zorgt er wel voor dat fr een beetje door de war komen */
	}

	section {
		height: 100vh;
		width: 100vw;
		/* voorkomt dat alles aan elkaar wordt geplakt */
		flex: none;
	}

	span {
		/* juiste font ipv proxima nova */
		font-family: 'Philosopher', sans-serif;
		-webkit-text-fill-color: transparent;
		background: linear-gradient(190deg, rgba(255, 255, 255, 0) 0%, rgba(255, 255, 255, 1) 100%);
		background-clip: text;
	}

	.achternaam h1,
	.voornaam h1 {
		position: absolute;
	}

	.naam {
		display: grid;
		grid-template-columns: 1fr;
		grid-template-rows: repeat(2, 0.5fr);
		grid-template-areas:
			'voornaam'
			'achternaam'
			'.';
		grid-area: naam;
		/* TODO: achtergrond weghalen */
		/* background: #afbfb7; */
	}

	.achternaam {
		grid-area: achternaam;
		position: relative;
		/* om de naam in het midden te krijgen */
		display: flex;
		justify-content: flex-end;
		align-items: flex-start;
	}

	.achternaam__video {
		transform: translate(100px, 0);
	}

	.voornaam {
		grid-area: voornaam;
		position: relative;
		/* om de naam in het midden te krijgen */
		display: flex;
		justify-content: center;
		align-items: flex-end;
	}

	.knoppen {
		display: flex;
		gap: 1rem;
		justify-self: center;
		align-self: center;
		grid-area: knoppen;
		background: #463b47;
	}

	.plaatje {
		grid-area: plaatje;
	}

	h1 span {
		display: inline-block;
		opacity: 0;
		/* animation: animate 1s linear forwards; */
		animation: myanimation 2s linear 0s 1 normal forwards;
	}

	@keyframes myanimation {
		0% {
			opacity: 0;
			transform: rotateY(90deg);
			filter: blur(10px);
		}
		100% {
			opacity: 1;
			transform: rotateY(0deg);
			filter: blur(0px);
		}
	}

	h1 span:nth-child(1) {
		animation-delay: 1.5s;
	}
	h1 span:nth-child(2) {
		animation-delay: 2s;
	}
	h1 span:nth-child(3) {
		animation-delay: 2.5s;
	}
	h1 span:nth-child(4) {
		animation-delay: 3s;
	}
	h1 span:nth-child(5) {
		animation-delay: 3.5s;
	}
	h1 span:nth-child(6) {
		animation-delay: 4s;
	}
</style>
