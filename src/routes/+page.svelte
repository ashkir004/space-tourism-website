<script lang="ts">
    import Navbar from "$lib/components/layout/Navbar.svelte";
    import bgHomeDesktop from "$lib/assets/home/background-home-desktop.jpg";
    import bgHomeTablet from "$lib/assets/home/background-home-tablet.jpg";
    import bgHomeMobile from "$lib/assets/home/background-home-mobile.jpg";
</script>

<picture class="fixed min-h-screen min-w-screen z-[-1]">
    <source srcset={bgHomeDesktop} media="(min-width: 64rem)" />
    <source srcset={bgHomeTablet} media="(min-width: 48rem)" />
    <img src={bgHomeMobile} alt="Background" class="absolute inset-0 w-full h-full object-cover" />
</picture>
<header>
    <Navbar />
</header>
<main class="flex flex-col  h-screen w-screen">
    <section class=" p-6 grid grid-cols-1 grid-rows-2 h-screen w-screen gap-12 
        lg:grid-cols-2 lg:grid-rows-1 lg:gap-0 lg:justify-items-center lg:items-center">

        <article class="text-center lg:text-start  flex flex-col gap-6 items-center justify-start md:justify-end 
            lg:justify-center lg:items-start">
            <p class="text-label text-primary-foreground/80 ">So, you want to travel to</p>
            <h1 class="text-display uppercase text-primary-foreground">Space</h1>
            <p class="text-body text-primary-foreground/80 md:max-w-lg lg:text-start">Let's face it; if you want to go to space, you might as well genuinely go to outer space and not hover kind of on the edge of it. Well sit back, and relax because we'll give you a truly out of this world experience!</p>
        </article>

        <div class=" flex flex-col items-center justify-start md:justify-start lg:justify-center">
            <button class="bg-secondary text-secondary-foreground rounded-full min-h-36 min-w-36
                md:min-h-68 md:min-w-68 aspect-ratio-circle
                text-heading uppercase">
                Explore
            </button>
        </div>
    </section>
</main>

