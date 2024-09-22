<script>
	import Navbar from '../../components/navigation/navbar.svelte';
	import Footer from '../../components/navigation/footer.svelte';
	import data from '$lib/data.json';

	const BACKGROUND = data.staff.background.src;
	const PARTNERS = data.partners.list;

	import { onMount } from 'svelte';

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
<div class="bg-cover bg-center bg-fixed" style="background-image: url('{BACKGROUND}');">
	<div
		class="partners grid md:grid-cols-3 grid-cols-1 grid-rows-auto gap-5 md:gap-0 mx-20 place-items-center h-screen"
	>
		{#each PARTNERS as partner}
			<div class="text-center">
				<img
					src={partner.image.src}
					alt={partner.image.alt}
					class={`w-full shadow-lg mask ${partner.image.mask === 'mask-square' ? 'rounded-3xl' : partner.image.mask}`}
				/>
				<h1 class="text-4xl text-center font-bold">{partner.name}</h1>
			</div>
		{/each}
	</div>
</div>

<Footer />
