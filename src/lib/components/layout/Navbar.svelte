<script lang="ts">
    import Logo from "../../assets/shared/logo.svg";
    import Nav from "./Nav.svelte";
    import Menu from "./Menu.svelte";

	import MenuControls from "../ui/MenuControls.svelte";
    import { cn } from "$lib/utils/utils";

    interface NavbarProps {
        class?: string;
    }

    let { class: className = '',
     }: NavbarProps = $props();

     let menuOpen = $state(false);

     function toggle() {
         menuOpen = !menuOpen;
     }

</script>

<div class={cn(`grid grid-cols-1 grid-rows-1 lg:pl-10 lg:pt-8`, className)}>
    <div class="col-span-full row-span-full flex flex-row items-center justify-start lg:justify-between gap-6 md:min-h-24 py-4 md:py-0 pl-4">

        <button class="grow-0 mx-4">
            <img src={Logo} alt="Logo" class="max-w-10" />
        </button>

        <Nav class="md:max-w-full lg:max-w-2xl xl:max-w-3xl 2xl:max-w-5xl px-10
        bg-transparent justify-end lg:justify-end 2xl:justify-center" />
        
        <MenuControls isOpen={menuOpen} toggle={toggle} class="md:hidden ml-auto mr-6 md:mr-15 {menuOpen ? 'hidden' : ''}" />
    </div>
    <Menu isOpen={menuOpen} toggle={toggle} class="md:hidden {!menuOpen ? 'hidden' : ''} " />
</div>