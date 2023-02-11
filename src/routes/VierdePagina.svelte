<script lang="ts">
	import { onMount } from 'svelte';

	// import type { PageData } from './$types';

	// export let data: PageData;

	onMount(() => {
		const buttons = document.querySelectorAll(
			'[data-carousel-button]'
		) as NodeListOf<HTMLDataElement>;
		buttons.forEach((button) => {
			button.addEventListener('click', () => {
				const offset = button.dataset.carouselButton === 'next' ? 1 : -1;
				// dichtstbijzijnde parent element met het data-element data-carousel en dan naar het ul element(met alle slides erin)
				const slides = button
					.closest('[data-carousel]') // parent element (dus de carousel)
					?.querySelector('[data-slides]') as HTMLUListElement;

				const activeSlide = slides?.querySelector('[data-active]') as HTMLLIElement;
				const rightSlide = slides?.querySelector('[data-right]') as HTMLLIElement;
				const leftSlide = slides?.querySelector('[data-left]') as HTMLLIElement;
				let newIndex = [...slides?.children].indexOf(activeSlide) + offset;

				if (newIndex < 0) newIndex = slides.children.length - 1;
				// leftIndex = slides.children.length - 2;

				if (newIndex >= slides.children.length) newIndex = 0;
				// rightIndex = 1;

				let leftIndex = newIndex - 1;
				if (newIndex == 0) leftIndex = slides.children.length - 1;

				let rightIndex = newIndex + 1;
				if (newIndex === slides.children.length - 1) rightIndex = 0;

				(slides.children[newIndex] as HTMLLIElement).dataset.active = 'true';
				(slides.children[rightIndex] as HTMLLIElement).dataset.right = 'true';
				(slides.children[leftIndex] as HTMLLIElement).dataset.left = 'true';

				delete activeSlide.dataset.active;
				delete rightSlide.dataset.right;
				delete leftSlide.dataset.left;
			});
		});
	});
</script>

<div class="vierde-pagina-grid-container">
	<div class="titel"><h1>Projecten</h1></div>

	<div class="projecten">
		<div class="carousel" data-carousel>
			<button class="carousel-button prev" data-carousel-button="prev">&#10140;</button>
			<button class="carousel-button next" data-carousel-button="next">&#10140;</button>
			<ul data-slides class="slide-list">
				<!-- middelste slide -->
				<li class="slide" data-active>
					<a href="/projecten/nieuws-app">
						<img
							src="https://images.unsplash.com/photo-1512941937669-90a1b58e7e9c?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwxfDB8MXxyYW5kb218MHx8fHx8fHx8MTY3MzkwMjgzNA&ixlib=rb-4.0.3&q=80&utm_campaign=api-credit&utm_medium=referral&utm_source=unsplash_source&w=1080"
							alt="Nieuws app"
						/>
						<h2>Nieuws App</h2>
					</a>
				</li>
				<!-- eerste rechter slide -->
				<li class="slide" data-right>
					<a href="/projecten/regen-analyse"
						><img
							src="https://images.unsplash.com/photo-1442120108414-42e7ea50d0b5?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwxfDB8MXxyYW5kb218MHx8fHx8fHx8MTY3NTA5MDI2NA&ixlib=rb-4.0.3&q=80&utm_campaign=api-credit&utm_medium=referral&utm_source=unsplash_source&w=1080"
							alt="Voorspelling regenval Australie"
						/>
						<h2>Regenvoorspelling</h2>
					</a>
				</li>
				<!-- eerste linker slide -->
				<li class="slide" data-left>
					<a href="/projecten/voedselconsumptie"
						><img
							src="https://images.unsplash.com/photo-1546069901-ba9599a7e63c?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwxfDB8MXxyYW5kb218MHx8fHx8fHx8MTY3MzkyMDQ4OA&ixlib=rb-4.0.3&q=80&utm_campaign=api-credit&utm_medium=referral&utm_source=unsplash_source&w=1080"
							alt="Analyse voedsel globale voedselconsumptie"
						/>
						<h2>Globale voedselconsumptie</h2>
					</a>
				</li>
				<!-- <li class="slide">
					<img
						src="https://images.unsplash.com/photo-1675315576622-97bf816e9cd8?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwxfDB8MXxyYW5kb218MHx8fHx8fHx8MTY3NTM0NzQ3NA&ixlib=rb-4.0.3&q=80&utm_campaign=api-credit&utm_medium=referral&utm_source=unsplash_source&w=1080"
						alt="Random foto 3"
					/>
				</li> -->
			</ul>
		</div>
	</div>

	<a href="#pagina3" class="pijlLinks">
		<i class="fa-solid fa-chevron-left" />
	</a>
</div>

<style>
	h2 {
		font-family: 'Great Vibes', cursive;
		font-size: xx-large;
		position: absolute;
	}

	img {
		border-radius: 2em;
		object-fit: cover;
		opacity: 0.6;
		/* aspect-ratio: 16/9; */
	}

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
			font-size: 3rem;
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

	.vierde-pagina-grid-container {
		width: 100%;
		height: 100%;
		display: grid;
		grid-template-columns: 0.3fr minmax(0, 3.2fr) 0.3fr;
		grid-template-rows: 0.3fr 1fr minmax(0, 1.5fr) 0.8fr 0.3fr;
		grid-auto-columns: 1fr;
		gap: 0px 0em;
		grid-auto-flow: row;
		grid-template-areas:
			'. . .'
			'. titel .'
			'. projecten .'
			'. projecten . '
			'. . .';
		position: relative;
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

	.titel {
		grid-area: titel;
	}

	.projecten {
		grid-area: projecten;
	}

	.carousel {
		width: 100%;
		height: 100%;
		position: relative;
		perspective: 600px;
	}

	.slide-list {
		position: absolute;
		transform-style: preserve-3d;
		width: 80%;
		max-width: 800px;
		height: 100%;
		left: 0;
		right: 0;
		margin-left: auto;
		margin-right: auto;
	}

	.slide {
		position: absolute;
		inset: 0;
		opacity: 0;
		/* transition: 200ms opacity ease-in-out; */
		/* transition-delay: 800ms; */
		/* width: calc(100% / 3);
		height: calc(100% / 2); */
		width: calc(100% / 2);

		margin: auto;
		aspect-ratio: 16/9;
	}

	.slide[data-active] {
		opacity: 1;
		z-index: 1;
		transition-delay: 200ms;
		transition: 200ms opacity linear;
	}

	.slide[data-left] {
		opacity: 0.5;
		z-index: 0;
		transition: 500ms transform linear;
		transform: translateX(-120%) rotateY(-30deg) translateZ(-100px);
	}
	.slide[data-right] {
		opacity: 0.5;
		z-index: 0;
		transition: 500ms transform linear;
		transform: translateX(120%) rotateY(30deg) translateZ(-100px);
	}

	.slide img {
		display: block;
		width: 100%;
		height: 100%;
		object-fit: cover;
		object-position: center;
		border-radius: 4em;
	}

	.carousel-button {
		position: absolute;
		z-index: 1;
		background: none;
		border: none;
		font-size: 4rem;
		bottom: 0;
		/* transform: translateY(-50%); */
		color: rgba(255, 255, 255, 0.5);
		border-radius: 0.25rem;
		padding: 0 0.5rem;
		/* background-color: rgba(0, 0, 0, 0); */
	}

	.carousel-button:hover,
	.carousel-button:focus {
		color: white;
		/* background-color: rgba(0, 0, 0, 0.2); */
	}

	.carousel-button:focus {
		/* outline: 1px solid black; */
	}

	.carousel-button.next {
		right: 30%;
	}
	.carousel-button.prev {
		left: 30%;
		transform: rotateY(180deg);
	}

	@media (max-width: 800px) {
		.slide[data-left] {
			/* transition: 500ms transform linear; */
			transform: translateY(-120%) rotateX(-30deg) translateZ(-100px);
		}

		.slide[data-right] {
			/* transition: 500ms transform linear; */
			transform: translateY(120%) rotateX(30deg) translateZ(-100px);
		}

		.carousel-button.prev {
			left: 2rem;
			top: 30%;
		}
		.carousel-button.next {
			right: 2rem;
			top: 30%;
		}

		.slide-list {
			width: 100%;
		}
	}
</style>
