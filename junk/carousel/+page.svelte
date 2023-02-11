<script lang="ts">
	// import type { PageData } from './$types';

	// export let data: PageData;
	let toggle = false;
</script>

<div class="scene">
	<div
		class="card"
		class:is-flipped={toggle}
		on:click={() => (toggle = !toggle)}
		on:keypress={() => (toggle = !toggle)}
	>
		<div class="card__face card__face--front">front</div>
		<div class="card__face card__face--back">back</div>
	</div>
</div>

<style>
	.scene {
		width: 200px;
		height: 260px;
		perspective: 600px;
	}

	.card {
		width: 100%;
		height: 100%;
		cursor: pointer;
		position: relative;
		/* transition heeft alleen een start en een begin */
		transition: transform 1s;
		/* hierdoor blijft de perspective behouden in the descendants */
		transform-style: preserve-3d;
		transform-origin: center right;
	}

	.card__face {
		position: absolute;
		height: 100%;
		width: 100%;
		backface-visibility: hidden;
		text-align: center;
		line-height: 260px;
	}

	.card__face--front {
		background: red;
	}

	.card__face--back {
		background: blue;
		transform: rotateY(180deg);
	}

	.card.is-flipped {
		/* volgorde transformatie is van belang */
		transform: translateX(-100%) rotateY(-180deg);
	}
</style>
