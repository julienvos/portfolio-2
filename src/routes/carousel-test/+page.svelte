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

<div class="carousel" data-carousel>
	<button class="carousel-button prev" data-carousel-button="prev">Prev</button>
	<button class="carousel-button next" data-carousel-button="next">Next</button>
	<ul data-slides class="slide-list">
		<li class="slide" data-active>
			<img
				src="https://images.unsplash.com/photo-1675186883824-a14b5c5d8da2?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwxfDB8MXxyYW5kb218MHx8fHx8fHx8MTY3NTM0NzQ0Nw&ixlib=rb-4.0.3&q=80&utm_campaign=api-credit&utm_medium=referral&utm_source=unsplash_source&w=1080"
				alt="Random foto 1"
			/>
		</li>
		<li class="slide" data-right>
			<img src="http://unsplash.it/g/800?random&blur&gravity=center" alt="Random foto 2" />
		</li>

		<li class="slide" data-left>
			<img
				src="https://images.unsplash.com/photo-1675315576622-97bf816e9cd8?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwxfDB8MXxyYW5kb218MHx8fHx8fHx8MTY3NTM0NzQ3NA&ixlib=rb-4.0.3&q=80&utm_campaign=api-credit&utm_medium=referral&utm_source=unsplash_source&w=1080"
				alt="Random foto 3"
			/>
		</li>
		<li class="slide">
			<img
				src="https://images.unsplash.com/photo-1675315576622-97bf816e9cd8?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwxfDB8MXxyYW5kb218MHx8fHx8fHx8MTY3NTM0NzQ3NA&ixlib=rb-4.0.3&q=80&utm_campaign=api-credit&utm_medium=referral&utm_source=unsplash_source&w=1080"
				alt="Random foto 3"
			/>
		</li>
	</ul>
</div>

<style>
	.carousel {
		width: 100vw;
		height: 100vh;
		position: relative;
		perspective: 600px;
	}

	.slide-list {
		position: absolute;
		transform-style: preserve-3d;
		width: 100%;
		height: 100%;
	}

	.slide {
		position: absolute;
		inset: 0;
		opacity: 0;
		/* transition: 200ms opacity ease-in-out; */
		/* transition-delay: 800ms; */
		width: calc(100% / 3);
		height: calc(100% / 2);
		margin: auto;
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

	.slide > img {
		display: block;
		width: 100%;
		height: 100%;
		object-fit: cover;
		object-position: center;
		border-radius: 4em;
	}

	.carousel-button {
		position: absolute;
		z-index: 2;
		background: none;
		border: none;
		font-size: 4rem;
		top: 50%;
		transform: translateY(-50%);
		color: rgba(255, 255, 255, 0.5);
		border-radius: 0.25rem;
		padding: 0 0.5rem;
		background-color: rgba(0, 0, 0, 0.1);
	}

	.carousel-button:hover,
	.carousel-button:focus {
		color: white;
		background-color: rgba(0, 0, 0, 0.2);
	}

	.carousel-button:focus {
		outline: 1px solid black;
	}

	.carousel-button.next {
		right: 1rem;
	}
	.carousel-button.prev {
		left: 1rem;
	}
</style>
