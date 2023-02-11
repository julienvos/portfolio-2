<script lang="ts">
	import DetailPagina from '../../../lib/components/DetailPagina.svelte';
</script>

<DetailPagina>
	<span slot="titel">Analyse regenval Australie</span>
	<p slot="tekst">
		Lorem ipsum dolor, sit amet consectetur adipisicing elit. Molestias qui ipsum unde provident
		doloribus vitae ab reprehenderit culpa ipsam ullam minima neque, at, deserunt earum nostrum
		dolorem tenetur corrupti, nemo perspiciatis optio suscipit sunt temporibus. Libero eum quae
		architecto labore praesentium id, autem impedit, officiis corporis minima quibusdam eligendi
		adipisci amet eius excepturi error iure quo neque nesciunt voluptatem veniam consequatur minus.
		Quasi natus, eveniet vitae exercitationem recusandae accusamus temporibus delectus id ut
		veritatis quisquam fugit? Voluptates odio corporis quibusdam necessitatibus porro animi.
		Nesciunt animi distinctio beatae dolore corporis esse eius ea sint illo vero et eaque
		voluptatibus sunt pariatur, blanditiis quisquam tempore odio vitae incidunt at autem magnam odit
		suscipit voluptatem? Officia ipsum repellat recusandae quis nisi ipsam a sunt sint maiores
		adipisci, doloremque autem commodi, sit nam ut repudiandae quibusdam suscipit laudantium
		voluptates maxime perspiciatis facilis? Nisi natus, sit quasi temporibus alias expedita libero
		quisquam ab commodi, quibusdam nobis perferendis in dicta vel beatae quaerat, sunt ratione.
		Nulla nostrum eos in suscipit amet.
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
