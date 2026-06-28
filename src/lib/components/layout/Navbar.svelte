<script lang="ts">
    import Logo from "../../assets/shared/logo.svg";
    // import Nav from "./Nav.svelte";

	import MenuControls from "../ui/MenuControls.svelte";
    import { cn } from "$lib/utils/utils";

    interface NavbarProps {
        class?: string;
        menuOpen?: boolean;
        toggle?: () => void;
    }

    let { class: className = '',
        menuOpen = false,
        toggle = () => {}
     }: NavbarProps = $props();

</script>

<div class={cn(`grid grid-cols-1 grid-rows-1`, className)}>
    <div class="col-span-full row-span-full flex flex-row items-center justify-start lg:justify-start py-8">

        <button>
            <img src={Logo} alt="Logo" class="min-w-5" />
        </button>

        <!-- <div class="flex flex-row items-center justify-end gap-12 lg:w-full">
            <Nav class="hidden lg:flex lg:flex-row gap-12" />
        </div> -->
        
        <MenuControls isOpen={menuOpen} toggle={toggle} class="lg:hidden ml-auto mr-6 md:mr-15 {menuOpen ? 'hidden' : ''}" />
    </div>
</div>