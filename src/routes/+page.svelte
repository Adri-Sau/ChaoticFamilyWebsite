<script>
	import Navbar from '../components/navigation/navbar.svelte';
	import Footer from '../components/navigation/footer.svelte';
	import Background from '../components/utils/background.svelte';

	const BLACK = 'https://upload.wikimedia.org/wikipedia/commons/4/49/A_black_image.jpg';

	const content = [
		{
			image: 'https://picsum.photos/seed/random/200',
			text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed non risus. Suspendisse lectus tortor, dignissim sit amet, adipiscing nec, ultricies sed, dolor. Cras elementum ultrices diam. Maecenas ligula massa, varius a, semper congue, euismod non, mi.',
			align: 'left',
			mask: 'mask-squircle'
		},
		{
			image: 'https://picsum.photos/seed/ciao/200',
			text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed non risus. Suspendisse lectus tortor, dignissim sit amet, adipiscing nec, ultricies sed, dolor. Cras elementum ultrices diam. Maecenas ligula massa, varius a, semper congue, euismod non, mi.',
			align: 'right',
			mask: 'mask-hexagon-2'
		},
		{
			image: 'https://picsum.photos/seed/no/200',
			text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed non risus. Suspendisse lectus tortor, dignissim sit amet, adipiscing nec, ultricies sed, dolor. Cras elementum ultrices diam. Maecenas ligula massa, varius a, semper congue, euismod non, mi.',
			align: 'left',
			mask: 'mask-circle'
		},
		{
			image: 'https://picsum.photos/seed/prova/200',
			text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed non risus. Suspendisse lectus tortor, dignissim sit amet, adipiscing nec, ultricies sed, dolor. Cras elementum ultrices diam. Maecenas ligula massa, varius a, semper congue, euismod non, mi.',
			align: 'right',
			mask: 'mask-square'
		}
	];
</script>

<Navbar />
<Background background="https://picsum.photos/seed/chaotic/1920/1080" />

<div class="flex-grow">
	<div class="container mx-auto my-8 grid grid-cols-1 gap-8">
		{#each content as item}
			<div
				class="flex flex-col md:flex-row {item.align === 'left'
					? 'md:flex-row-reverse'
					: ''} items-center md:items-start"
			>
				<div class="md:w-1/4 p-4">
					<img
						src={item.image}
						alt="Placeholder"
						class={`w-full shadow-lg mask ${item.mask} ${item.mask === 'mask-square' ? 'rounded-3xl' : ''}`}
					/>
				</div>
				<div class="md:w-1/4 p-4">
					<p class="text-lg font-semibold">{item.text}</p>
				</div>
			</div>
		{/each}
	</div>
</div>

<Footer />
