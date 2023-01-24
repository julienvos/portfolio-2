<script lang="ts">
	// import type { PageData } from './$types';

	// export let data: PageData;
	import video from '$lib/assets/video/smoke.mp4';
</script>

<div class="titel-section">
	<video src={video} autoplay muted>
		<track kind="captions" />
	</video>
	<h1>
		<span>J</span>
		<span>U</span>
		<span>L</span>
		<span>I</span>
		<span>E</span>
		<span>N</span>
	</h1>
</div>

<style>
	.titel-section {
		background: black;
		display: grid;
		justify-content: center;
		align-content: center;
		height: 100vh;
		position: relative;
	}
	h1 {
		letter-spacing: 0.2em;
		position: absolute;
		justify-self: center;
		align-self: center;

		/* HOORT HIER NIET! */
		/* background: linear-gradient(190deg, rgba(255, 255, 255, 0) 0%, rgba(255, 255, 255, 1) 100%);
		color: transparent;
		background-clip: text; */
	}

	/* hier hoort de kleur in te zitten voor de gradient NIET bij h1 */
	span {
		background: linear-gradient(190deg, rgba(255, 255, 255, 0) 0%, rgba(255, 255, 255, 1) 100%);
		color: transparent;
		background-clip: text;
	}

	h1 span {
		display: inline-block;
		opacity: 0;
		/* animation: animate 1s linear forwards */
		animation: myanimation 2s linear 0s 1 normal forwards;
	}

	video {
		object-fit: cover;
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
		animation-delay: 1 s;
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
