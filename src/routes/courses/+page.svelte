<script>
	import Navbar from '../../components/navigation/navbar.svelte';
	import Footer from '../../components/navigation/footer.svelte';

	const BACKGROUND = 'https://picsum.photos/seed/chaotic/1920/1080';
</script>

<Navbar />
<div class="bg-[url('{BACKGROUND}')] bg-cover bg-center bg-fixed h-screen -z-10">
	<div class="grid grid-cols-2 grid-rows-2 gap-20 place-items-center h-screen">
		<div>1</div>
		<div>2</div>
		<div>3</div>
		<div>4</div>
	</div>
</div>

<Footer />
