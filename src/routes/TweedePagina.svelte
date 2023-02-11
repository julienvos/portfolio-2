<script lang="ts">
	import { onMount } from 'svelte';
	import { index } from '$lib/stores/indexStore';

	let observer: IntersectionObserver;

	let visible: boolean;

	onMount(async () => {
		observer = new IntersectionObserver((entries) => {
			entries.forEach((entry) => {
				if (entry.isIntersecting) {
					// (entry.target as HTMLElement).classList.add('start-animation');
					visible = true;
					observer.unobserve(entry.target);
				}
			});
		});

		const items = document.querySelectorAll('li');
		items.forEach((item) => observer.observe(item));
	});
</script>

<div class="tweede-pagina__grid-container">
	<div class="tweede-pagina__titel">
		<h1 class:tracking-in-contract={visible}>Wie ben ik?</h1>
	</div>

	<div class="tweede-pagina__tekst">
		<ul class="tekst">
			<li class:start-animation={visible}>28 Jaar</li>
			<li class:start-animation={visible}>Zwartsluis, Overijssel</li>
			<li class:start-animation={visible}>Bewegingswetenschappen MSc</li>
			<li class:start-animation={visible}>Voormalig IT Trainee YoungCapital NEXT</li>
			<li class:start-animation={visible}>Interesse Techniek & Gezondheid</li>
		</ul>
	</div>

	<a href="#pagina3" class="pijlRechts">
		<i class="fa-solid fa-chevron-right" />
	</a>

	<a href="#pagina1" class="pijlLinks">
		<i class="fa-solid fa-chevron-left" />
	</a>
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
	}

	.start-animation {
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
		grid-template-columns: 0.3fr minmax(0, 1.5fr) minmax(0, 1.2fr) 0.3fr;
		grid-template-rows: 0.3fr 0.6fr minmax(0, 2.7fr) 0.4fr;
		grid-auto-columns: 1fr;
		grid-auto-rows: 1fr;
		gap: 0px 0em;
		grid-auto-flow: row;
		grid-template-areas:
			'. . . .'
			'. titel titel .'
			'. tekst . .'
			'. . . .';

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
		right: 2em;
		top: 50%;
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
		left: 2em;
		top: 50%;
	}

	.tweede-pagina__titel {
		grid-area: titel;
	}

	.tweede-pagina__tekst {
		grid-area: tekst;

		padding: 4em;
	}

	@media only screen and (max-width: 880px) {
		.tweede-pagina__grid-container {
			grid-template-columns: 0.3fr minmax(0, 1.7fr) 0.3fr;
			grid-template-rows: 0.3fr 0.5fr minmax(0, 1fr) 0.5fr;
			grid-template-areas:
				'. . .'
				'titel titel titel'
				'pijlLinks tekst pijlRechts'
				'. . .';
		}
		.tweede-pagina__tekst {
			padding: 0 0em;
			text-align: center;
		}

		.tweede-pagina__titel {
			text-align: center;
		}
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
</style>
