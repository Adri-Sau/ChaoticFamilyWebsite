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

<div class="drawer drawer-end sticky top-0 z-50">
	<input id="my-drawer-1" type="checkbox" class="drawer-toggle" />
	<div class="drawer-content">
		<div
			class="p-2 px-4 full navbar bg-base-200 flex sticky top-0 z-20 shadow-[0_5px_2px_0_rgba(0,0,0,0.5)]"
		>
			<div class="navbar-start">
				<a href={prelink('/')}>
					<img
						src={prelink('/LogoChaoticTrasparente.png')}
						alt="Logo Chaotic Family"
						class="rounded w-16 hover:scale-110 transition-transform duration-100 select-none"
					/>
				</a>
			</div>

			<div class="navbar-center">
				<ul class="menu menu-horizontal text-xl font-bold hidden sm:flex">
					<li>
						<a href={prelink('/')} class="btn btn-ghost text-xl select-none">Home</a>
					</li>
					<li>
						<a href={prelink('/courses')} class="btn btn-ghost text-xl select-none">Courses</a>
					</li>
					<li>
						<a href={prelink('/staff')} class="btn btn-ghost text-xl select-none">Staff</a>
					</li>
					<li>
						<a href={prelink('/shop')} class="btn btn-ghost text-xl select-none">Shop</a>
					</li>
					<li>
						<a href={prelink('/partners')} class="btn btn-ghost text-xl select-none">Partners</a>
					</li>
				</ul>
			</div>

			<div class="navbar-end">
				<label
					for="my-drawer-1"
					aria-label="open sidebar"
					class="btn btn-square btn-ghost flex sm:hidden"
				>
					<svg
						xmlns="http://www.w3.org/2000/svg"
						fill="none"
						viewBox="0 0 24 24"
						class="inline-block w-6 h-6 stroke-current"
						><path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M4 6h16M4 12h16M4 18h16"
						></path></svg
					>
				</label>
			</div>
		</div>

		<!-- Page content here -->
		<slot />
	</div>

	<div class="drawer-side">
		<label for="my-drawer-1" aria-label="close sidebar" class="drawer-overlay"></label>
		<ul class="menu p-4 w-40 min-h-full bg-base-200 text-base-content pt-20">
			<li>
				<a href={prelink('/')} class="btn btn-ghost text-xl">Home</a>
			</li>
			<li>
				<a href={prelink('/courses')} class="btn btn-ghost text-xl">Courses</a>
			</li>
			<li>
				<a href={prelink('/staff')} class="btn btn-ghost text-xl">Staff</a>
			</li>
			<li>
				<a href={prelink('/shop')} class="btn btn-ghost text-xl">Shop</a>
			</li>
			<li>
				<a href={prelink('/partners')} class="btn btn-ghost text-xl">Partners</a>
			</li>
		</ul>
	</div>
</div>
