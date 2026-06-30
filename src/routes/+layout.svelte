<script lang="ts">
	import './layout.css';
	import favicon from '$lib/assets/favicon-32x32.png';

	import Navbar from "$lib/components/layout/Navbar.svelte";
    import bgHomeDesktop from "$lib/assets/home/background-home-desktop.jpg";
    import bgHomeTablet from "$lib/assets/home/background-home-tablet.jpg";
    import bgHomeMobile from "$lib/assets/home/background-home-mobile.jpg";

	let { children } = $props();
</script>

<svelte:head><link rel="icon" href={favicon} /></svelte:head>

<div class="overflow-hidden">
	<picture class="fixed min-h-screen min-w-screen z-[-1]">
		<source srcset={bgHomeDesktop} media="(min-width: 64rem)" />
    <source srcset={bgHomeTablet} media="(min-width: 48rem)" />
    <img src={bgHomeMobile} alt="Background" class="absolute inset-0 w-full h-full object-cover" />
	</picture>
<header>
    <Navbar />
</header>

{@render children()}
</div>

