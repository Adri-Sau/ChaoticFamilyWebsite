<script>
	import Navbar from '../components/navigation/navbar.svelte';
	import Footer from '../components/navigation/footer.svelte';
	import data from '$lib/data.json';

	const BACKGROUND = data.home.background.src;

	const PARAGRAPHS = data.home.paragraphs;
</script>

<Navbar />

<div class="flex-grow bg-cover bg-center bg-fixed" style="background-image: url('{BACKGROUND}');">
	<div class="container mx-auto py-8 grid grid-cols-1 gap-8">
		{#each PARAGRAPHS as paragraph}
			<div
				class="flex flex-col md:flex-row {paragraph.image.align === 'left'
					? 'md:flex-row-reverse'
					: ''} items-center md:items-start"
			>
				<div class="md:w-1/4 p-4 shadow-lg">
					<img
						src={paragraph.image.src}
						alt={paragraph.image.alt}
						class={`w-full mask ${paragraph.image.mask === 'mask-square' ? 'rounded-3xl' : paragraph.image.mask}`}
					/>
				</div>
				<div class="md:w-1/4 p-4">
					<p class="text-lg font-semibold text-center">{paragraph.text}</p>
				</div>
			</div>
		{/each}
	</div>
</div>
<Footer />
