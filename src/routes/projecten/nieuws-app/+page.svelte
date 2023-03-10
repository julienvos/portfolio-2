<script lang="ts">
	import DetailPagina from '../../../lib/components/DetailPagina.svelte';

	// import type { PageData } from '../nieuws-app/$types';

	// export let data: PageData;

	// importeer alle images
	const imageModules = import.meta.glob('$lib/assets/images/nieuws-app-images/*.png', {
		as: 'url'
	});
	console.log(Object.keys(imageModules));

	// for (const path in imageModules) {
	// 	imageModules[path]().then((mod) => {
	// 		console.log(path, mod);
	// 	});
	// }

	import theImage from '$lib/assets/images/nieuws-app-images/Screenshot_1652362499.png';
	import secondImage from '$lib/assets/images/nieuws-app-images/Screenshot_1653059860.png';
	console.log(theImage);
	// haal alle imageUrls op
	// let imageUrls: string[] = Object.keys(imageModules);

	let imageUrls: string[] = [theImage, secondImage];

	import '$lib/swiper-cards.css';
</script>

<DetailPagina>
	<span slot="titel">Nieuws App</span>
	<div slot="tekst">
		<a href="https://github.com/julienvos/flutter_news_app" class="link"
			>Klik hier op het project te bekijken op Github</a
		>
		<br />
		<br />

		<p>
			Mobiele apps zijn tegenwoordig niet meer weg te denken vandaag de dag. Naast het feit dat het
			aantal apps met de dag groeit, groeien ook de mogelijkheden om apps te bouwen. Een vrij nieuwe
			methode van apps bouwen op zowel Android als IOS is doormiddel van Dart en het bijbehorende
			framework Flutter. Dit systeem is ontwikkeld door Google en heeft de ambitie om met één keer
			de code voor een app te schrijven, waarnaar dit gepubliseerd kan worden over verscheidene
			systemen (o.a. web/IOS/Android/Windows).
			<br />
			<br />
			In het huidige project wordt doormiddel van Flutter een nieuws app gebouwd. Het gaat hierbij om
			een app voor zowel Android als IOS. De gebruiker wordt verwelkomd door een introductie scherm,
			kan vervolgens inloggen en krijgt daarna een intuitive interface om nieuws content te bekijken.
			<br />
			Flutter vind ik persoonlijk een toegankelijk framework, waar je al snel zelf projecten kan in starten.
			Qua programmeren is het een combinatie van Java en Javascript. Een app is hierbij opgebouwd uit
			zogenoemde Widgets (in React zijn dat components).
		</p>
	</div>

	<div slot="app">
		<swiper-container class="mySwiper" effect="cards" grab-cursor="true">
			<!-- img src moet in javascript geimporteerd worden -->
			{#each imageUrls as item}
				<swiper-slide><img src={item} alt="Foto van de app" /></swiper-slide>
			{/each}
		</swiper-container>
	</div>
</DetailPagina>

<style>
	.link {
		color: lightblue;
		text-decoration: underline;
	}

	/* h1 { */
	/* juiste font ipv proxima nova */
	/* font-family: 'Philosopher', sans-serif;
		-webkit-text-fill-color: transparent;
		background: linear-gradient(190deg, rgba(255, 255, 255, 0) 0%, rgba(255, 255, 255, 1) 100%);
		background-clip: text;
		height: 100%;
	} */

	img {
		object-fit: cover;
		max-height: 100%;
		border-radius: 2em;
	}
</style>
