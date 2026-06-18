<script lang="ts">
    import Header from '$lib/components/Header.svelte';
	import About from '$lib/components/About.svelte';
</script>

<main>
    <h1 class="sr-only">Room homepage</h1>
    <Header />
    <About />
</main>

<style>
    main {
        display: grid;
        grid-template-columns: 1fr;
        grid-template-rows: 1fr;
    }


</style>
