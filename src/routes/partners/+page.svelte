<script>
    import Background from '../../components/utils/background.svelte';
    import Navbar from '../../components/navigation/navbar.svelte';
    import Footer from '../../components/navigation/footer.svelte';
</script>

<Navbar />
<Background background="https://picsum.photos/seed/chaotic/1920/1080" />

<div class="flex-grow">
    some content
</div>

<Footer />