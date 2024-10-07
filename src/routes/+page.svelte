<script>
	import Navbar from '$lib/navigation/navbar.svelte';
	import Footer from '$lib/navigation/footer.svelte';
	import data from '$lib/data.json';
	import { dev } from '$app/environment';

	const BACKGROUND = data.home.background.src;
	const PARAGRAPHS = data.home.paragraphs;

	/**
	 * @param {string} src
	 */
	function prelink(src) {
		if (dev) {
			return src;
		}
		return `/ChaoticFamilyWebsite${src}`;
	}
</script>

<Navbar />

<div
	class="flex-grow bg-cover bg-center bg-fixed"
	style="background-image: url('{prelink(BACKGROUND)}');"
>
	<div class="container mx-auto py-8 grid grid-cols-1 gap-8">
		{#each PARAGRAPHS as paragraph}
			<div
				class="flex flex-col md:flex-row {paragraph.image.align === 'left'
					? 'md:flex-row-reverse'
					: ''} items-center md:items-start"
			>
				<div class="md:w-1/4 drop-shadow-lg">
					<img
						src={prelink(paragraph.image.src)}
						alt={paragraph.image.alt}
						class={`w-full mask select-none ${paragraph.image.mask === 'mask-square' ? 'rounded-3xl' : paragraph.image.mask}`}
					/>
				</div>
				<div class="md:w-1/4 p-4">
					<p class="text-lg font-semibold text-center align-middle select-none">{paragraph.text}</p>
				</div>
			</div>
		{/each}
	</div>
</div>
<Footer />
