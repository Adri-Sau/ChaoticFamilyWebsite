<script>
	import Navbar from '../../components/navigation/navbar.svelte';
	import Footer from '../../components/navigation/footer.svelte';
	import data from '$lib/data.json';

	const BACKGROUND = data.courses.background.src;
	const COURSES = data.courses.list;
</script>

<Navbar />
<div
	class="bg-cover bg-center bg-fixed h-screen -z-10"
	style="background-image: url('{BACKGROUND}');"
>
	<div class="grid grid-cols-2 grid-rows-auto gap-20 place-items-center h-screen">
		{#each COURSES as course}
			<div class="relative text-center">
				<img
					src={course.image.src}
					alt={course.image.alt}
					class={`w-full shadow-lg mask ${course.image.mask} ${course.image.mask === 'mask-square' ? 'rounded-3xl' : ''}`}
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
