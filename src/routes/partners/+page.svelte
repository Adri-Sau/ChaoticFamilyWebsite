<script>
	import Navbar from '../../components/navigation/navbar.svelte';
	import Footer from '../../components/navigation/footer.svelte';
	import data from '$lib/data.json';

	const BACKGROUND = data.staff.background.src;
	const PARTNERS = data.partners.list;
</script>

<Navbar />
<div class="bg-cover bg-center bg-fixed" style="background-image: url('{BACKGROUND}');">
	<div
		class="grid md:grid-cols-3 grid-cols-1 grid-rows-auto gap-5 md:gap-0 mx-20 place-items-center h-screen"
	>
		{#each PARTNERS as partner}
			<div />
			<div class="text-center">
				<img
					src={partner.image.src}
					alt={partner.image.alt}
					class={`w-full shadow-lg mask ${partner.image.mask} ${partner.image.mask === 'mask-square' ? 'rounded-3xl' : ''}`}
				/>
				<h1 class="text-4xl text-center font-bold">{partner.name}</h1>
			</div>
		{/each}
	</div>
</div>

<Footer />
