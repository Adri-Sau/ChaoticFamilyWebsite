<script>
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

<div class="w-full flex flex-col items-center absolute top-1/2 -translate-y-1/2">
	<img
		src={prelink('/LogoChaoticTrasparente.png')}
		alt="Logo Chaotic Family"
		class="relative rounded w-36 opacity-50 animate-[spin_3s_linear_infinite] select-none"
	/>
	<div class="absolute top-1/2 -translate-y-1/2 flex flex-col items-center text-center select-none">
		<h1 class="text-4xl font-bold">Coming Soon</h1>
		<p class="text-md">We are working hard to bring you the best experience.</p>
	</div>
</div>
