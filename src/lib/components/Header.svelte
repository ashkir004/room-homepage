<script>
    import logo from '$lib/assets/images/logo.svg';
    import iconHamburger from '$lib/assets/images/icon-hamburger.svg';
    import iconClose from '$lib/assets/images/icon-close.svg';

    let menuOpen = $state(false);

    function toggleNavigation() {
        menuOpen = !menuOpen;
    }
</script>

<header class="site-header">
    <button class="site-header__hamburger {menuOpen ? 'hidden-mobile' : ''} hidden-desktop" aria-label="Toggle navigation"
        onclick={toggleNavigation}
    >
        <img src={iconHamburger} alt="Hamburger menu icon" />
    </button>
    <div class="site-header__logo {menuOpen ? 'hidden-mobile' : ''}">
        <img src={logo} alt="Room homepage logo" />
    </div>
    <nav class="site-header__nav {menuOpen ? '' : 'hidden-mobile'}">
        <button class="site-header__close hidden-desktop" aria-label="Close navigation"
            onclick={toggleNavigation}
        >
            <img src={iconClose} alt="Close menu icon" />
        </button>
        <ul class="site-header__links">
            <li class="site-header__item"><a href="#home" class="site-header__link">Home</a></li>
            <li class="site-header__item"><a href="#shop" class="site-header__link">Shop</a></li>
            <li class="site-header__item"><a href="#about" class="site-header__link">About</a></li>
            <li class="site-header__item"><a href="#contact" class="site-header__link">Contact</a></li>
        </ul>
    </nav>
</header>

<style>

.site-header {
    display: grid;
    grid-template-columns: auto 1fr auto;
    align-items: center;
    min-height: var(--space-1375);
}

.site-header__hamburger, .site-header__close {
    background: transparent;
    border: none;
    cursor: pointer;
}

.site-header__hamburger {
    grid-column: 1 / 2;
    margin-inline-start: var(--space-200);
     
    @media (min-width: 21rem) { margin-inline-start: var(--space-300); }
}

.site-header__logo {
    grid-column: 2 / 3;
    justify-self: center;
    margin-inline-end: var(--space-200);
}

.site-header__nav {
    grid-column: 1 / -1;
    background-color: var(--white);
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    min-height: var(--space-1375);
    padding-inline: var(--space-200);

    @media (min-width: 21rem) {
        padding-inline: var(--space-300);
    }
}

.site-header__links {
    list-style: none;
    display: flex;
    flex-direction: row;
    gap: var(--space-200);

    @media (min-width: 21rem) {
        gap: var(--space-300);
    }
}

.site-header__item {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: var(--space-100);
    padding-block-start: var(--space-100);
}

.site-header__item a {
    text-decoration: none;
    color: var(--black);
}

.site-header__item::after {
    content: "";
    display: block;
    width: 0;
    height: 2px;
    background-color: transparent;
    transition: width 200ms ease-in;
}

.site-header__item:hover::after {
    width: var(--space-300);
    background-color: var(--black);
}

.hidden-mobile {
    display: none;
}

@media (min-width: 48.1rem) {
    .hidden-mobile {
        display: block;
    }

    .hidden-desktop {
        display: none;
    }

    .site-header {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: flex-start;
        min-height: fit-content;
    }

    .site-header__nav {
        background-color: transparent;
        min-height: fit-content;
    }

    .site-header__item a {
        color: var(--white);
    }

    .site-header__item:hover::after {
        background-color: var(--white);
    }
}
</style>