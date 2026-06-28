<script lang="ts">
    import Navbar from "$lib/components/layout/Navbar.svelte";
    import bgHomeDesktop from "$lib/assets/home/background-home-desktop.jpg";
    import bgHomeTablet from "$lib/assets/home/background-home-tablet.jpg";
    import bgHomeMobile from "$lib/assets/home/background-home-mobile.jpg";
</script>

<header>
    <picture class="fixed min-h-screen min-w-screen z-[-1]">
        <source srcset={bgHomeDesktop} media="(min-width: 1024px)" />
        <source srcset={bgHomeTablet} media="(min-width: 768px)" />
        <img src={bgHomeMobile} alt="Background" class="absolute inset-0 w-full h-full object-cover" />
    </picture>
    <Navbar />
</header>
