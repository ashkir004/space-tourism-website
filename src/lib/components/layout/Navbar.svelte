<script lang="ts">
    import Logo from "../../assets/shared/logo.svg";
    import Nav from "./Nav.svelte";

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

<div class={cn(`grid grid-cols-1 grid-rows-1 outline-1`, className)}>
    <div class="col-span-full row-span-full flex flex-row items-center justify-between md:min-h-24 py-4 md:py-0 pl-4">

        <button>
            <img src={Logo} alt="Logo" class="max-w-10" />
        </button>

        <Nav class="justify-self-stretch" />
        
        <MenuControls isOpen={menuOpen} toggle={toggle} class="md:hidden ml-auto mr-6 md:mr-15 {menuOpen ? 'hidden' : ''}" />
    </div>
</div>