<script lang="ts">
	// // import type { PageData } from './$types';

	// // export let data: PageData;

	// // bind gebruiken
	// // var carousel = document.querySelector<HTMLElement>('.carousel');
	// // var cells = carousel?.querySelectorAll<HTMLElement>('.carousel__cell');
	// // var cellWidth = carousel?.offsetWidth;

	// // console.log(cellWidth);
	// let carousel: HTMLDivElement;

	// // console.log(carousel); //moet met onMount

	// // let carousel: HTMLDivElement;
	// // let wi = carousel.offsetWidth;

	// let selectedIndex = 0;
	// let cellCount = 9; // aantal items

	// let theta: number, radius: number;

	// // let cellWidth = 500;
	// // carouselRadius is nodig voor translateZ(-{carouselRadius})
	// // let carouselRadius = Math.round(cellWidth / 2 / Math.tan(Math.PI / numberOfCells));

	// // function rotateCarousel() {
	// // 	var angle = theta * selectedIndex * -1;
	// // 	carousel!.style.transform = 'translateZ(' + -radius + 'px) ' + 'rotateY' + '(' + angle + 'deg)';
	// // }

	// let r = 588;

	// let h: number;
	// let w: number;
	// let numberOfCells = 9;
	// // let cellWidth = w - 20;

	// onMount(() => {
	// 	console.log(w);
	// 	// let cellWidth = w - 20;
	// 	// // 2 * pi = 360 graden
	// 	// let radius = Math.round(cellWidth / 2 / Math.tan((Math.PI * 2) / numberOfCells / 2));

	// 	// let cells = carousel.querySelectorAll<HTMLElement>('.carousel__cell'); // Je moet <HTMLElement> hier expliciet benoemen om de style te krijgen van een cell
	// 	// cells.forEach((cell) => {
	// 	// 	let i = 0;
	// 	// 	// 40 komt van 360 / 9 cells
	// 	// 	let cellAngle = i * 40;
	// 	// 	cell.style.transform = 'rotateY' + '(' + cellAngle + 'deg) translateZ(' + radius + 'px)';
	// 	// 	i++;
	// 	// });
	// 	// for ( var i=0; i < cells.length; i++ ){
	// 	// 	let cell = cells[i];
	// 	// 	cell.style.transform = rotateFn + '(' + cellAngle + 'deg) translateZ(' + radius + 'px)';
	// 	// }
	// });
</script>

<div class="scene">
	<!-- 3D space -->
	<div class="carousel">
		<!-- 3D object -->
		<div class="carousel__cell"><h1>1</h1></div>
		<!-- 3D face -->
		<div class="carousel__cell">2</div>
		<div class="carousel__cell">3</div>
		<div class="carousel__cell">4</div>
		<div class="carousel__cell">5</div>
		<div class="carousel__cell">6</div>
		<div class="carousel__cell">7</div>
		<div class="carousel__cell">8</div>
		<div class="carousel__cell">9</div>
	</div>
</div>

<!-- <p style="text-align: center;">
	<button
		class="previous-button"
		on:click={() => {
			selectedIndex--;
			rotateCarousel();
		}}>Previous</button
	>
	<button
		class="next-button"
		on:click={() => {
			selectedIndex++;
			rotateCarousel();
		}}>Next</button
	>
</p> -->
<style>
	.scene {
		/* 100% binnen bijvoorbeeld een grid */
		width: 100%; /* 210px */
		height: 100%; /* 140px */
		perspective: 1000px;
		position: relative;
		margin: 40px auto;
	}

	.carousel {
		/* 100% binnen de scene */
		width: 100%;
		height: 100%;
		position: absolute;
		transform-style: preserve-3d;
		transform: translateZ(-588px);
		transition: transform 1s;
	}

	.carousel__cell {
		position: absolute;
		/* -20 px omdat er een gap van 2x 10px tussen zit (zowel horizontaal als verticaal) */
		width: calc(100% - 20px);
		height: calc(100% - 20px);
		left: 10px;
		top: 10px;
	}

	.carousel__cell:nth-child(1) {
		background-color: hsla(0, 100%, 50%, 0.8);
		/* zegmaar roteren en afstoten */
		/* iedere keer +40 graden (vanwege 360 / 9)  (waarbij 9 het aantal cellen is) */
		transform: rotateY(0deg) translateZ(588px);
	}
	.carousel__cell:nth-child(2) {
		background-color: hsla(40, 100%, 50%, 0.8);
		transform: rotateY(40deg) translateZ(588px);
	}
	.carousel__cell:nth-child(3) {
		background-color: hsla(80, 100%, 50%, 0.8);
		transform: rotateY(80deg) translateZ(588px);
	}
	.carousel__cell:nth-child(4) {
		background-color: hsla(120, 100%, 50%, 0.8);
		transform: rotateY(120deg) translateZ(588px);
	}
	.carousel__cell:nth-child(5) {
		background-color: hsla(160, 100%, 50%, 0.8);
		transform: rotateY(160deg) translateZ(588px);
	}
	.carousel__cell:nth-child(6) {
		background-color: hsla(200, 100%, 50%, 0.8);
		transform: rotateY(200deg) translateZ(588px);
	}
	.carousel__cell:nth-child(7) {
		background-color: hsla(240, 100%, 50%, 0.8);
		transform: rotateY(240deg) translateZ(588px);
	}
	.carousel__cell:nth-child(8) {
		background-color: hsla(280, 100%, 50%, 0.8);
		transform: rotateY(280deg) translateZ(588px);
	}
	.carousel__cell:nth-child(9) {
		background-color: hsla(320, 100%, 50%, 0.8);
		transform: rotateY(320deg) translateZ(588px);
	}
</style>
