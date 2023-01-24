<script lang="ts">
	// import type { PageData } from './$types';

	// export let data: PageData;
</script>

<div class="grid-container">
	<div class="content1">Content 1</div>
	<div class="content2">content 2</div>
	<div class="content3">content 3</div>
</div>

<style>
	.grid-container {
		display: grid;
		height: 100vh;
		grid-auto-columns: 1fr;
		grid-template-columns: repeat(4, 1fr);
		grid-template-rows: repeat(4, 1fr);
		gap: 0px 0em;
		grid-template-areas:
			'. content1 content1 .'
			'. . content3 .'
			'. . . .'
			'. content2 . .';
	}

	.content1 {
		grid-area: content1;
		background-color: aquamarine;
	}
	.content2 {
		grid-area: content2;
		background-color: azure;
	}
	.content3 {
		grid-area: content3;
		background-color: brown;
	}
	.content4 {
		grid-area: content4;
		background-color: cyan;
	}

	@media only screen and (max-width: 550px) {
		.grid-container {
			grid-template-columns: 1fr;
			grid-template-rows: 1fr 1fr 1fr;
			grid-template-areas:
				'content1'
				'content2'
				'content3';
		}
	}
</style>
