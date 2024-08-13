<script>
	export let background;
</script>

<div
	class="relative bg-fixed bg-center bg-cover bg-no-repeat h-screen"
	style={`background-image: url(${background}); z-index: 10`}
>
	<slot />
</div>
