<script lang="ts">
    import * as Tabs from '$lib/components/ui/tabs/index';
    import imageEuropaWebp from '$lib/assets/destination/image-europa.webp';
    import imageMarsWebp from '$lib/assets/destination/image-mars.webp';
    import imageMoonWebp from '$lib/assets/destination/image-moon.webp';
    import imageTitanWebp from '$lib/assets/destination/image-titan.webp';
    import imageEuropaPng from '$lib/assets/destination/image-europa.png';
    import imageMarsPng from '$lib/assets/destination/image-mars.png';
    import imageMoonPng from '$lib/assets/destination/image-moon.png';
    import imageTitanPng from '$lib/assets/destination/image-titan.png';

    let triggerFocusClasses = `text-primary-foreground/80 rounded-none border-0
            border-b-2 border-transparent transition-border duration-300 ease-in-out
            focus:outline-none focus:ring-0
            active:outline-none active:ring-0
            focus-visible:outline-none focus-visible:ring-0
            data-active:text-primary-foreground
            data-active:bg-transparent 
            data-active:border-0 data-active:border-b-2 data-active:border-primary-foreground/80 
    `;

    let DestinationContent = [
        {
            id: 1,
            name: 'Moon',
            value: 'moon',
            content: "See our planet as you've never seen it before. A perfect relaxing trip away to help regain perspective and come back refreshed. While you're there, take in some history by visiting the Luna 2 and Apollo 11 landing sites.",
            averageDistance: '384,400 km',
            estimatedTravelTime: '3 days',
        },
        {
            id: 2,
            name: 'Mars',
            value: 'mars',
            content: "Don't forget to pack your hiking boots. You'll need them to tackle Olympus Mons, the tallest planetary mountain in our solar system. It's two and a half times the size of Everest!",
            averageDistance: '225 mil. km',
            estimatedTravelTime: '9 months',
        },
        {
            id: 3,
            name: 'Europa',
            value: 'europa',
            content: "The smallest of the four Galilean moons orbiting Jupiter, Europa is a winter lover's dream. With an icy surface, it's perfect for a bit of ice skating, curling, hockey, or simple relaxation in your snug wintery cabin.",
            averageDistance: '628 mil. km',
            estimatedTravelTime: '3 years',
        },
        {
            id: 4,
            name: 'Titan',
            value: 'titan',
            content: "The only moon known to have a dense atmosphere other than Earth, Titan is a home away from home (just a few hundred degrees colder!). As a bonus, you get striking views of the Rings of Saturn.",
            averageDistance: '1.6 bil. km',
            estimatedTravelTime: '7 years',
        },
    ];

</script>

<main class="h-screen flex flex-col gap-6 justify-center lg:grid lg:grid-rows-[auto_1fr] lg:items-start border-2 bg-border-primary p-8 md:p-10 lg:p-12">
    <div class="flex flex-row gap-6">
        <span class="text-label text-primary-foreground/50">01</span>
        <h1 class="text-label uppercase">Pick your destination</h1>
    </div>
    <article class="flex flex-col gap-8 items-center justify-between
        lg:flex-row lg:gap-24 lg:items-center lg:justify-center lg:max-w-6xl lg:mx-auto">
        <picture>
            <source srcset={imageMoonWebp} type="image/webp" />
            <source srcset={imageMoonPng} type="image/png" />
            <img src={imageMoonPng} alt="moon" class="w-48 md:w-72 lg:w-96" />
        </picture>
        <Tabs.Root value="moon" class="border-2 bg-border-primary">
            <Tabs.List class="bg-transparent text-primary-foreground/80 text-label gap-8 self-center lg:self-start">
                <Tabs.Trigger value="moon" class={`uppercase cursor-pointer ${triggerFocusClasses}`}><p class="mb-4">Moon</p></Tabs.Trigger>
                <Tabs.Trigger value="mars" class={`uppercase cursor-pointer ${triggerFocusClasses}`}><p class="mb-4">Mars</p></Tabs.Trigger>
                <Tabs.Trigger value="europa" class={`uppercase cursor-pointer ${triggerFocusClasses}`}><p class="mb-4">Europa</p></Tabs.Trigger>
                <Tabs.Trigger value="titan" class={`uppercase cursor-pointer ${triggerFocusClasses}`}><p class="mb-4">Titan</p></Tabs.Trigger>
            </Tabs.List>
            {#each DestinationContent as { name, value, content, averageDistance, estimatedTravelTime } (value)}
                <Tabs.Content value={value} class="flex flex-col gap-6 max-w-md md:max-w-lg lg:max-w-lg text-center lg:text-start">
                    <h2 class="text-display uppercase">{name}</h2>
                    <p class="text-body text-primary-foreground/80">{content}</p>
                    <hr />
                    <div>
                        <div class="flex flex-col justify-center gap-4 md:flex-row md:justify-around lg:justify-start md:gap-12 lg:gap-24">
                            <div class="flex flex-col gap-2">
                                <h3 class="text-label uppercase text-primary-foreground/50">Avg. Distance</h3>
                                <p class="text-heading uppercase">{averageDistance}</p>
                            </div>
                            <div class="flex flex-col gap-2">
                                <h3 class="text-label uppercase text-primary-foreground/50">Est. Travel Time</h3>
                                <p class="text-heading uppercase">{estimatedTravelTime}</p>
                            </div>
                        </div>
                    </div>
                </Tabs.Content>
            {/each}
            
        </Tabs.Root>
    </article>
</main>

<!-- <Tabs.Content value="titan" class="flex flex-col gap-6">
                <h2 class="text-display uppercase">Titan</h2>
            </Tabs.Content> -->