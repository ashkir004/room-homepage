<script lang="ts">
    import Header from '$lib/components/Header.svelte';
	import About from '$lib/components/About.svelte';
    import aboutFurnitureDark from '$lib/assets/images/image-about-dark.jpg';
    import aboutFurnitureLight from '$lib/assets/images/image-about-light.jpg';
</script>

<main>
    <h1 class="sr-only">Room homepage</h1>
    <Header />
    <About />
    <div class="about__furniture hello">
        <div class="about__furniture-img">
            <img src={aboutFurnitureDark} alt="About our furniture" />
        </div>
        <div class="about__furniture-content">
            <h2 class="about__furniture-title">About our furniture</h2>
            <p class="about__furniture-text text-3-medium">
                Our multifunctional collection blends design and function to suit your individual taste. Make each room unique, or pick a cohesive theme that best express your interests and what inspires you. Find the furniture pieces you need, from traditional to contemporary styles or anything in between. Product specialists are available to help you create your dream space. 
            </p>
        </div>
        <div class="about__furniture-img">
            <img src={aboutFurnitureLight} alt="About our furniture" />
        </div>
    </div>
</main>

<style>
    main {
        display: grid;
        grid-template-columns: 1fr;
        grid-template-rows: auto;
    }

    .about__furniture {
        background-color: var(--white);
        grid-column: 1 / -1;
        grid-row: 2 / -1;
        display: flex;
        flex-direction: column;
        min-width: 100%;
    }

    .about__furniture-img {
        display: block;
        width: 100%;
    }

    .about__furniture-img img {
        display: block;
        width: 100%;
        height: 100%;
        object-fit: cover;
    }

    .about__furniture-content {
        display: flex;
        flex-direction: column;
        gap: var(--space-200);
        padding: var(--space-600) var(--space-400);
    }

    .about__furniture-title {
        color: var(--black);
        text-transform: uppercase;
        font-size: calc(14 / 16 * 1rem);
        font-weight: var(--font-bold);
        letter-spacing: calc(5.83 / 16 * 1rem);
    }

    .about__furniture-text {
        color: var(--grey-500);
    }

    @media (min-width: 48rem) {

        .about__furniture-content {
            padding: var(--space-800);
        }

        .about__furniture img {
            width: 100%;
            height: auto;
            aspect-ratio: 2 / 1;
            object-position: center;
        }
    }

    @media (min-width: 64rem) {
        main {
            grid-template-columns: 1fr;
            grid-template-rows: min(80vh, 700px) auto;
        }

        .about__furniture {
            grid-column: 1 / -1;
            grid-row: 2 / -1;
            display: grid;
            grid-template-columns: 1fr 2fr 1fr;
        }

        .about__furniture-img img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
    }

</style>
