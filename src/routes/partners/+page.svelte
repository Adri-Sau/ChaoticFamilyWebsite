<script>
	import Navbar from '$lib/navigation/navbar.svelte';
	import Footer from '$lib/navigation/footer.svelte';
	import data from '$lib/data.json';
	import { onMount } from 'svelte';
	import { dev } from '$app/environment';

	const BACKGROUND = data.staff.background.src;
	const PARTNERS = data.partners.list;

	/**
	 * @param {any} href
	 */
	function prelink(href) {
		if (dev) {
			return href;
		}
		return `/ChaoticFamilyWebsite${href}`;
	}

	function insertEmptyDivs() {
		const isMdBreakpoint = window.innerWidth >= 768;

		if (isMdBreakpoint) {
			const container = document.querySelector('.partners');
			if (container) {
				const childDivs = container.querySelectorAll('div');

				childDivs.forEach((div) => {
					const emptyDiv = document.createElement('div');

					container.insertBefore(emptyDiv, div);
				});
			}
		}
	}

	onMount(() => {
		insertEmptyDivs();

		const handleResize = () => {
			const container = document.querySelector('.partners');
			if (container) {
				const emptyDivs = container.querySelectorAll('.empty');
				emptyDivs.forEach((div) => div.remove());

				insertEmptyDivs();
			}
		};

		window.addEventListener('resize', handleResize);

		// Cleanup function when component is destroyed
		return () => {
			window.removeEventListener('resize', handleResize);
		};
	});
</script>

<Navbar />
<div class="bg-cover bg-center bg-fixed" style="background-image: url('{prelink(BACKGROUND)}');">
	<div
		class="partners grid md:grid-cols-3 grid-cols-1 grid-rows-auto gap-5 md:gap-0 mx-20 place-items-center h-screen"
	>
		{#each PARTNERS as partner}
			<div class="text-center">
				<img
					src={prelink(partner.image.src)}
					alt={partner.image.alt}
					class={`w-full drop-shadow-lg mask ${partner.image.mask === 'mask-square' ? 'rounded-3xl' : partner.image.mask}`}
				/>
				<h1 class="text-4xl text-center font-bold">{partner.name}</h1>
			</div>
		{/each}
	</div>
</div>

<Footer />
