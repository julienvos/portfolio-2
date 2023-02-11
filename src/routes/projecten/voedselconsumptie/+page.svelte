<script lang="ts">
	import DetailPagina from '$lib/components/DetailPagina.svelte';
	// import type { PageData } from './$types';

	// export let data: PageData;
</script>

<DetailPagina>
	<span slot="titel">Voedsel consumptie</span>
	<p slot="tekst">
		Lorem ipsum dolor sit amet consectetur adipisicing elit. Nostrum dolorem tenetur quae? Similique
		architecto molestias facilis voluptates, voluptate natus nulla dicta quasi commodi cupiditate
		quod praesentium fuga dolorum, laudantium vitae ea veritatis harum provident quae sint rem neque
		magnam, explicabo deserunt. Neque tempore inventore atque officia natus odio, mollitia quia
		facilis sequi doloribus doloremque quod reiciendis, eos officiis dolore cumque iure est
		repudiandae quos aspernatur architecto dolorum quam. Fuga deleniti accusantium eligendi maiores
		totam animi temporibus eius dolore? Aliquid tempore eveniet soluta quas consequuntur facere
		praesentium distinctio in deserunt molestias officia eius, fugiat a repellat nulla cumque, harum
		blanditiis necessitatibus. Itaque et porro totam ea excepturi assumenda architecto dolore
		perspiciatis ab, minus asperiores? Delectus est soluta, possimus necessitatibus sunt consectetur
		enim at totam hic minus velit et corrupti iste aperiam culpa nostrum quae, eos temporibus
		tempore consequatur odit dignissimos aut quod. Dolores cum officia placeat sapiente nisi quam
		ipsam ratione atque obcaecati illo pariatur blanditiis facere porro doloremque accusamus
		temporibus, ad animi aperiam optio beatae nostrum deserunt amet! Aspernatur, perferendis rem.
		Labore recusandae tempora quasi animi debitis nostrum eaque sequi cum, nulla repellat at, sint
		obcaecati porro quia deleniti eos deserunt, dolor accusantium repellendus quas vero quidem non!
		Esse, deserunt.
	</p>
	<img slot="app" src="http://unsplash.it/g/400?random&blur&gravity=center" alt="dit is een foto" />
</DetailPagina>

<style>
	img {
		border-radius: 2em;
		margin: 0 auto;
	}

	p {
		text-align: center;
	}
</style>
