<script lang="ts">
    import { cn } from "$lib/utils/utils";
    import * as NavigationMenu from "$lib/components/ui/navigation-menu/index";

    type variant = "main" | "menu";

    type NavProps = {
        class?: string;
        variant?: variant;
    }

    let {
        class: className= '',
        variant= "main",
    }: NavProps = $props();

    let RootBaseClass = `hidden md:flex bg-primary text-primary-foreground
        flex-row items-stretch justify-start gap-8
        text-labels-sm md:text-labels-md lg:text-labels-lg uppercase h-full`;

    let ListBaseClass = `flex flex-row items-stretch justify-start gap-12 h-full`;

    let ItemBaseClass = `border-b-2 border-b-transparent 
        hover:border-b-2 hover:border-b-secondary/50 focus:border-b-2 focus:border-b-secondary
        transition-colors duration-300 ease-in-out
        flex flex-col justify-center
    `;

    let activeItemClass = `border-b-2 border-b-foreground`;

    let activeItemClassMenuVariant = `border-0`;

    let linkBaseClass = `hover:bg-transparent hover:text-primary-foreground focus:bg-transparent focus:text-primary-foreground
    active:bg-transparent active:text-primary-foreground [&[data-active=true]]:bg-transparent [&[data-active=true]]:text-primary-foreground
    flex flex-row gap-3`;

    let navItems = [
        { id: 0, title: "Home", href: "/" },
        { id: 1, title: "Destination", href: "#destination" },
        { id: 2, title: "Crew", href: "#crew" },
        { id: 3, title: "Technology", href: "#technology" }
    ];

    let activeId = $state(1);
</script>
<NavigationMenu.Root class={cn(RootBaseClass, className)}>
    <span class="md:hidden absolute lg:block lg:w-50 lg:left-5 xl:w-[64%] xl:left-10 top-1/2 h-px -translate-x-full bg-gray-500 z-10 " aria-hidden="true"></span>
    <span class="absolute {variant === 'main' ? 'block' : 'hidden'} inset-0  bg-secondary/10 backdrop-blur-lg " aria-hidden="true"></span>
    <NavigationMenu.List class={cn(ListBaseClass, className)}>

        {#each navItems as navItem (navItem.id) }
            <NavigationMenu.Item class={cn(ItemBaseClass, 
                                        navItem.id === activeId ? activeItemClass : '', 
                                        variant === 'menu' ? activeItemClassMenuVariant : '')} onclick={() => activeId = navItem.id}>
                
                <NavigationMenu.Link href={navItem.href} class={cn(linkBaseClass)}>
                    <span class="font-bold">{navItem.id.toLocaleString().padStart(2, '0')}</span>{navItem.title}
                </NavigationMenu.Link>
            </NavigationMenu.Item>
        {/each}

    </NavigationMenu.List>
</NavigationMenu.Root>