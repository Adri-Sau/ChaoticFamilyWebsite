<script>
	import Navbar from '$lib/navigation/navbar.svelte';
	import Footer from '$lib/navigation/footer.svelte';
	import data from '$lib/data.json';

	const BACKGROUND = data.staff.background.src;
	const STAFF = data.staff.list;
	import { dev } from '$app/environment';

	/**
	 * @param {any} href
	 */
	function prelink(href) {
		if (dev) {
			return href;
		}
		return `/ChaoticFamilyWebsite${href}`;
	}
</script>

<Navbar />
<div class="bg-cover bg-center bg-fixed" style="background-image: url('{prelink(BACKGROUND)}');">
	<div
		class="grid md:grid-cols-5 grid-cols-1 grid-rows-auto gap-5 md:gap-0 mx-20 place-items-center md:h-screen py-8"
	>
		{#each STAFF as staff}
			<div class="relative text-center">
				<img
					src={prelink(staff.image.src)}
					alt={staff.image.alt}
					class={`w-full select-none drop-shadow-lg mask ${staff.image.mask === 'mask-square' ? 'rounded-3xl' : staff.image.mask}`}
				/>
				<div class="absolute w-full top-1/2 -translate-y-1/2">
					<h1 class="text-4xl text-center font-bold">{staff.name}</h1>
					<div>
						<div class="text-center text-xl select-none">{staff.role}</div>
					</div>
				</div>
			</div>
			<div />
		{/each}
	</div>
</div>

<Footer />
