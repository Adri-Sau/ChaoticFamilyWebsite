<script>
	import Navbar from '../../components/navigation/navbar.svelte';
	import Footer from '../../components/navigation/footer.svelte';
	import data from '$lib/data.json';

	const BACKGROUND = data.staff.background.src;
	const STAFF = data.staff.list;
</script>

<Navbar />
<div class="bg-cover bg-center bg-fixed" style="background-image: url('{BACKGROUND}');">
	<div
		class="grid md:grid-cols-5 grid-cols-1 grid-rows-auto gap-5 md:gap-0 mx-20 place-items-center h-screen"
	>
		{#each STAFF as staff}
			<div class="relative text-center">
				<img
					src={staff.image.src}
					alt={staff.image.alt}
					class={`w-full shadow-lg mask ${staff.image.mask} ${staff.image.mask === 'mask-square' ? 'rounded-3xl' : ''}`}
				/>
				<div class="absolute w-full top-1/2 -translate-y-1/2">
					<h1 class="text-4xl text-center font-bold">{staff.name}</h1>
					<div>
						<div class="text-center text-xl">{staff.role}</div>
					</div>
				</div>
			</div>
			<div />
		{/each}
	</div>
</div>

<Footer />
