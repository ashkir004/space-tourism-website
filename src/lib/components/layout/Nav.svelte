<script lang="ts">
    import { cn } from "$lib/utils/utils";
    import * as NavigationMenu from "$lib/components/ui/navigation-menu/index";

    type NavProps = {
        class?: string;
    }

    let {
        class: className= '',
    }: NavProps = $props();

    let RootBaseClass = `hidden md:flex bg-primary text-primary-foreground
        flex-row items-stretch justify-start gap-8
        text-labels-sm md:text-labels-md lg:text-labels-lg uppercase h-full
        `;

    let ListBaseClass = `flex flex-row items-stretch justify-start gap-12 h-full`;

    let ItemBaseClass = `border-b-2 border-b-transparent 
        hover:border-b-2 hover:border-b-secondary/50 focus:border-b-2 focus:border-b-secondary
        transition-colors duration-300 ease-in-out
        flex flex-col justify-center
    `;

    let activeItemClass = `border-b-2 border-b-foreground`;

    let linkBaseClass = `hover:bg-primary hover:text-primary-foreground focus:bg-primary focus:text-primary-foreground
    `;

    let navItems = [
        { id: 1, title: "Home", href: "/" },
        { id: 2, title: "Destination", href: "#destination" },
        { id: 3, title: "Crew", href: "#crew" },
        { id: 4, title: "Technology", href: "#technology" }
    ];

    let activeId = $state(1);
</script>

<NavigationMenu.Root class={cn(RootBaseClass, className)}>
    <NavigationMenu.List class={cn(ListBaseClass, className)}>

        {#each navItems as navItem (navItem.id) }
            <NavigationMenu.Item class={cn(ItemBaseClass, navItem.id === activeId ? activeItemClass : '')} onclick={() => activeId = navItem.id}>
                
                <NavigationMenu.Link href={navItem.href} class={cn(linkBaseClass)}>
                    {navItem.title}
                </NavigationMenu.Link>
            </NavigationMenu.Item>
        {/each}

    </NavigationMenu.List>
</NavigationMenu.Root>