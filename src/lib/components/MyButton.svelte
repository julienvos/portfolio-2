<script lang="ts">
	export let name: string = 'geen Naam';
	export let link: string | null = null;
	export let downloadFileName: string | null = null;
</script>

<a href={link} download={downloadFileName}>
	<button>
		<span />
		<span />
		<span />
		<span />
		{name}
	</button>
</a>

<style>
	button {
		position: relative;
		padding: 1em 1.8em;
		outline: none;
		border: 1px solid #303030;
		background: rgb(51, 65, 85);
		color: rgb(203, 213, 225);
		text-transform: uppercase;
		letter-spacing: 2px;
		font-size: 14px;
		overflow: hidden;
		transition: 0.2s;
		border-radius: 20px;
		cursor: pointer;
	}

	button:hover {
		box-shadow: 0 0 10px #9da1ac, 0 0 25px #001eff, 0 0 50px #4f5154;
		transform: scale(1.1);
		transition-delay: 0.6s;
	}

	button span {
		position: absolute;
	}

	button span:nth-child(1) {
		top: 0;
		left: -100%;
		width: 100%;
		height: 2px;
		background: linear-gradient(90deg, transparent, #35c291);
	}

	button:hover span:nth-child(1) {
		left: 100%;
		transition: 0.7s;
	}

	button span:nth-child(3) {
		bottom: 0;
		right: -100%;
		width: 100%;
		height: 2px;
		background: linear-gradient(90deg, transparent, #001eff);
	}

	button:hover span:nth-child(3) {
		right: 100%;
		transition: 0.7s;
		transition-delay: 0.35s;
	}

	button span:nth-child(2) {
		top: -100%;
		right: 0;
		width: 2px;
		height: 100%;
		background: linear-gradient(180deg, transparent, #09dab7);
	}

	button:hover span:nth-child(2) {
		top: 100%;
		transition: 0.7s;
		transition-delay: 0.17s;
	}

	button span:nth-child(4) {
		bottom: -100%;
		left: 0;
		width: 2px;
		height: 100%;
		background: linear-gradient(360deg, transparent, #001eff);
	}

	button:hover span:nth-child(4) {
		bottom: 100%;
		transition: 0.7s;
		transition-delay: 0.52s;
	}

	button:active {
		background: #ae00af;
		background: linear-gradient(to top right, #504a63, #8b92cc);
		color: #bfbfbf;
		box-shadow: 0 0 8px #292f33, 0 0 8px #001eff, 0 0 8px #3d1ca8;
		transition: 0.1s;
	}

	button:active span:nth-child(1) span:nth-child(2) span:nth-child(2) span:nth-child(2) {
		transition: none;
		transition-delay: none;
	}
</style>
