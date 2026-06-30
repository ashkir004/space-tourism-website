<script lang="ts">
    import { cn } from "$lib/utils";
    import MenuControls from "../ui/MenuControls.svelte";
    import Nav from "./Nav.svelte";

    
    type MenuProps = {
        class?: string;
        isOpen?: boolean;
        toggle?: () => void;
    }

    let {
        class: className= '',
        isOpen= false,
        toggle,
    }: MenuProps = $props();

</script>

<div class={cn("h-full w-2/3 fixed top-0 right-0 z-10 md:hidden", className)}>
    <span class="absolute block inset-0  bg-secondary/10 backdrop-blur-lg -z-10" aria-hidden="true"></span>
    <div class="flex flex-col gap-16">
        <MenuControls isOpen={isOpen} toggle={toggle} class="ml-auto mr-6 mt-6 md:mr-15"  />
        <Nav class="flex flex-col bg-transparent gap-3 pl-3 md:pl-0" variant="menu" />
    </div>
</div>