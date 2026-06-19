<script lang="ts">
    import Header from '$lib/components/Header.svelte';
	import About from '$lib/components/About.svelte';
</script>

<main>
    <h1 class="sr-only">Room homepage</h1>
    <Header />
    <About />
    <div class="hello">Hello, World!</div>
</main>

<style>
    main {
        display: grid;
        grid-template-columns: 1fr;
        grid-template-rows: auto;
        min-height: 100vh;
    }

    .hello {
        background-color: var(--black);
        grid-column: 1 / -1;
        grid-row: 2 / -1;
    }

    @media (min-width: 64rem) {
        main {
            grid-template-columns: 1fr;
            grid-template-rows: min(80vh, 700px) auto;
        }
    }

    /* @media (min-width: 90rem) {
        main {
            grid-template-rows: min(80vh, 700px) auto;
        }
    } */


</style>
