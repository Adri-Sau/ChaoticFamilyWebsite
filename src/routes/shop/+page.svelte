<script>
	import Navbar from '$lib/navigation/navbar.svelte';
	import Footer from '$lib/navigation/footer.svelte';
	import Comingsoon from '$lib/comingsoon.svelte';
	import data from '$lib/data.json';
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

	const BACKGROUND = data.merch.background.src;
</script>

<Navbar />
<div
	class="bg-cover bg-center bg-fixed h-screen -z-10"
	style="background-image: url('{prelink(BACKGROUND)}');"
>
	<Comingsoon />
</div>
<Footer />
