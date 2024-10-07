<script>
	import Navbar from '$lib/navigation/navbar.svelte';
	import Footer from '$lib/navigation/footer.svelte';
	import data from '$lib/data.json';
	import { dev } from '$app/environment';

	const BACKGROUND = data.courses.background.src;
	const COURSES = data.courses.list;

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
<div
	class="bg-cover bg-center bg-fixed z-10"
	style="background-image: url('{prelink(BACKGROUND)}');"
>
	<div
		class="grid md:grid-cols-2 grid-cols-1 grid-rows-auto gap-20 place-items-center md:h-screen py-8"
	>
		{#each COURSES as course}
			<div class="relative text-center drop-shadow-lg">
				<img
					src={prelink(course.image.src)}
					alt={course.image.alt}
					class={`w-full mask ${course.image.mask === 'mask-square' ? 'rounded-3xl' : course.image.mask}`}
				/>
				<div class="absolute w-full top-1/2 -translate-y-1/2">
					<h1 class="text-4xl text-center font-bold">{course.title}</h1>
					{#each course.trainings as training}
						<div>
							<div class="text-center text-xl">{training.day}</div>
							<div class="text-center">{training.time}</div>
						</div>
					{/each}
				</div>
			</div>
		{/each}
	</div>
</div>

<Footer />
