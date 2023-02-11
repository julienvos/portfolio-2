<script lang="ts">
	import MyButton from '$lib/components/MyButton.svelte';
	import video from '$lib/assets/video/smoke.mp4';
	import foto from '$lib/assets/images/portret-zwart-wit.jpeg';

	import cv from '$lib/assets/docs/CV-Julien Vos.pdf';
</script>

<div class="grid-container">
	<div class="naam">
		<div class="voornaam">
			<video src={video} autoplay muted>
				<track kind="captions" />
			</video>
			<h1>
				<span>J</span><span>U</span><span>L</span><span>I</span><span>E</span><span>N</span>
			</h1>
		</div>
		<div class="achternaam">
			<video class="achternaam__video" src={video} autoplay muted>
				<track kind="captions" />
			</video>
			<h1><span>V</span><span>O</span><span>S</span><span>.</span></h1>
		</div>
	</div>

	<a href="#pagina2" class="pijlRechts">
		<i class="fa-solid fa-chevron-right" />
	</a>

	<div class="knoppen">
		<MyButton name="CV" link={cv} downloadFileName={'CV-Julien-Vos'} />
		<MyButton name="Projecten" link="#pagina4" />
	</div>

	<div class="plaatje">
		<img src={foto} alt="portret foto" />
	</div>
</div>

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

		position: relative;
	}

	/* .pijlLinks {
		grid-area: pijlLinks;
		align-self: center;
		justify-self: center;
	} */

	.pijlRechts {
		/* grid-area: pijlRechts;
		opacity: 0.5;
		font-size: 3rem;
		align-self: center;
		justify-self: center; */

		position: absolute;
		top: 50%;
		right: 2em;
		opacity: 0.5;
		font-size: 3rem;
	}

	img {
		height: 100%;
		object-fit: cover;
	}
	video {
		object-fit: cover;
		max-height: 100%;
		z-index: -1;
		/* max-width: 100%; */
		/* aspect ratio zorgt er wel voor dat fr een beetje door de war komen */
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
		grid-template-rows: repeat(2, minmax(0, 0.5fr));
		grid-template-areas:
			'voornaam'
			'achternaam'
			'.';
		grid-area: naam;
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
		/* om er een row van te maken */
		display: flex;
		gap: 1rem;

		/* position in de grid */
		justify-self: center;
		align-self: center;
		grid-area: knoppen;
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

	@media only screen and (max-width: 860px) {
		.grid-container {
			position: relative;
			grid-template-columns: 1fr;
			gap: 0 0;
			grid-template-rows: 1.5fr minmax(0, 1fr) 0.5fr;
			grid-template-areas:
				'. . .'
				'. naam pijlRechts'
				'. knoppen .';
		}

		.naam {
			z-index: 1;
		}

		.plaatje {
			max-height: 100%;
			max-width: 100%;
			position: absolute;
			z-index: -1;
			margin: 0 auto;
		}

		.achternaam__video {
			/* om de uitstekende video weer terug te zetten  */
			transform: translate(0, 0);
			/* margin-right: -100px; */
		}
		.achternaam {
			justify-content: center;
		}

		video {
			opacity: 0.5;
			animation: opacity-change 4s linear 1 normal forwards;
		}

		@keyframes opacity-change {
			0% {
				opacity: 0.5;
			}

			70% {
				opacity: 0.3;
			}
			100% {
				opacity: 0;
			}
		}
	}
</style>
