<script lang="ts">
    import mobileHero1 from '$lib/assets/images/mobile-image-hero-1.jpg';
    import mobileHero2 from '$lib/assets/images/mobile-image-hero-2.jpg';
    import mobileHero3 from '$lib/assets/images/mobile-image-hero-3.jpg';
    import desktopHero1 from '$lib/assets/images/desktop-image-hero-1.jpg';
    import desktopHero2 from '$lib/assets/images/desktop-image-hero-2.jpg';
    import desktopHero3 from '$lib/assets/images/desktop-image-hero-3.jpg';
    import iconArrow from '$lib/assets/images/icon-arrow.svg';
    import iconAngleLeft from '$lib/assets/images/icon-angle-left.svg';
    import iconAngleRight from '$lib/assets/images/icon-angle-right.svg';

    let slide = $state(3);

    type SlideItem = {
        title: string;
        text: string;
        alt: string;
        image: {
            mobile: string;
            desktop: string;
        };
    };

    const imageRegistry: Record<string, string> = {
        'mobile-image-hero-1.jpg': mobileHero1,
        'mobile-image-hero-2.jpg': mobileHero2,
        'mobile-image-hero-3.jpg': mobileHero3,
        'desktop-image-hero-1.jpg': desktopHero1,
        'desktop-image-hero-2.jpg': desktopHero2,
        'desktop-image-hero-3.jpg': desktopHero3
    };

    function getImageUrl(imageName: string): string {
        return imageRegistry[imageName];
    }

    const slides: SlideItem[] = [
        {
            title: 'Discover innovative ways to decorate',
            text: 'We provide unmatched quality, comfort, and style for property owners across the country. Our experts combine form and function in bringing your vision to life. Create a room in your own style with our collection and make your property a reflection of you and what you love.',
            alt: 'Bright living room with modern sofa and decor',
            image: {
                mobile: 'mobile-image-hero-1.jpg',
                desktop: 'desktop-image-hero-1.jpg'
            }
        },
        {
            title: 'We are available all across the globe',
            text: 'With stores all over the world, it\'s easy for you to find furniture for your home or place of business. Locally, we\'re in most major cities throughout the country. Find the branch nearest you using our store locator. Any questions? Don\'t hesitate to contact us today.',
            alt: 'Three stylish chairs arranged in a clean interior',
            image: {
                mobile: 'mobile-image-hero-2.jpg',
                desktop: 'desktop-image-hero-2.jpg'
            }
        },
        {
            title: 'Manufactured with the best materials',
            text: 'Our modern furniture store provide a high level of quality. Our company has invested in advanced technology to ensure that every product is made as perfect and as consistent as possible. With three decades of experience in this industry, we understand what customers want for their home and office.',
            alt: 'Minimalist black chair with soft lighting',
            image: {
                mobile: 'mobile-image-hero-3.jpg',
                desktop: 'desktop-image-hero-3.jpg'
            }
        }
    ];

    function getCurrentSlide(): SlideItem {
        return slides[slide - 1] ?? slides[0];
    }

    function goNextSlide(): void {
        if (slide === slides.length) return;
        slide++;
    }

    function goPreviousSlide(): void {
        if (slide === 1) return;
        slide--;
    }

</script>

<div class="about">
    <h2 class="sr-only">Introduction section</h2>
    <div class="about-wrapper">

        <picture class="about__hero">
            <source media="(min-width: 48rem)" srcset={getImageUrl(getCurrentSlide().image.desktop)} />
            <img src={getImageUrl(getCurrentSlide().image.mobile)} alt={getCurrentSlide().alt} loading="eager" decoding="async" />
        </picture>

        <div class="slider">
            <button class="slider__previous" onclick={goPreviousSlide}>
                <img src={iconAngleLeft} alt="Previous slide" />
            </button>
            <button class="slider__next" onclick={goNextSlide}>
                <img src={iconAngleRight} alt="Next slide" />
            </button>
        </div>

        <div class="about-content-wrapper">
            <div class="about-content">
                <h3 class="about-content__title text-2">{getCurrentSlide().title}</h3>
                <p class="about-content__text text-3-medium">{getCurrentSlide().text}</p>
            </div>

            <div class="about-cta">
                <a href="#shop" class="about__link text-4">Shop now</a>
                <img src={iconArrow} alt="Arrow icon" />
            </div>
        </div>
                
    </div>
</div>

<style>
    .about {
        grid-column: 1 / -1;
        grid-row: 1 / -1;
        display: grid;
        grid-template-columns: 1fr;
        grid-template-rows: auto;
        background-color: var(--white);
    }
    
    .about-wrapper {
        display: grid;
        grid-template-columns: 1fr;
        grid-template-rows: auto;
    }

    .about__hero {
        display: block;
        width: 100%;
        object-fit: cover;
        grid-column: 1 / -1;
        grid-row: 1 / -1;
    }

    .about__hero img {
        display: block;
        width: 100%;
        height: auto;
    }

    .about-content-wrapper {
        color: var(--black);
        background-color: var(--white);
        padding: var(--space-800) var(--space-350);
        display: flex;
        flex-direction: column;
        gap: var(--space-400);
    }

    .about-content {
        display: flex;
        flex-direction: column;
        gap: var(--space-200);
    }

    .about-content__title {
        color: var(--black);
    }

    .about-content__text {
        color: var(--grey-500);
    }

    .about__link {
        color: var(--black);
        text-decoration: none;
        text-transform: uppercase;
    }

    .about-cta {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: space-between;
        gap: var(--space-300);
    }

    .slider {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: flex-end;
        background-color: transparent;
        grid-column: 1 / -1;
        grid-row: 1 / -1;
        align-self: flex-end;
    }

    .slider__previous, .slider__next {
        background-color: var(--black);
        border: none;
        cursor: pointer;
        padding: var(--space-300);
    }

    .slider__previous img, .slider__next img {
        display: block;
        width: var(--space-200);
        height: auto;
    }

@media (min-width: 48rem) {
    .about-cta {
        justify-content: flex-start;
        gap: var(--space-300);
    }

    .slider__previous, .slider__next {
        padding-inline: var(--space-500);
        padding-block: var(--space-400);
    }

    .slider__previous img, .slider__next img {
        width: var(--space-300);
    }
}

@media (min-width: 64rem) {
    .about-wrapper {
        grid-template-columns: repeat(2, 1fr);
        grid-template-rows: auto;
    }

    .about__hero {
        grid-column: 1 / 2;
        grid-row: 1 / -1;
    }

    .about__hero img {
        aspect-ratio: 1 / 1;
    }

    .about-content-wrapper {
        grid-column: 2 / -1;
        grid-row: 1 / -1;
        /* padding: var(--space-1400) var(--space-700); */
        padding-inline: var(--space-700);
        place-self: center;
        gap: var(--space-300);
    }

    .about-content {
        max-width: 25rem;
    }

    .about-content__title {
        max-width: 80%;
    }

    .slider {
        grid-column: 2 / -1;
        grid-row: 1 / -1;
        z-index: 999;
        justify-self: flex-start;
    }
}


</style>