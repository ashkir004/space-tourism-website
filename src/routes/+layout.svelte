<script lang="ts">
	import './layout.css';
	import favicon from '$lib/assets/favicon-32x32.png';
	import { page } from '$app/state';

	import Navbar from "$lib/components/layout/Navbar.svelte";
    import bgHomeDesktop from "$lib/assets/home/background-home-desktop.jpg";
    import bgHomeTablet from "$lib/assets/home/background-home-tablet.jpg";
    import bgHomeMobile from "$lib/assets/home/background-home-mobile.jpg";
	import bgDestinationDesktop from "$lib/assets/destination/background-destination-desktop.jpg";
	import bgDestinationTablet from "$lib/assets/destination/background-destination-tablet.jpg";
	import bgDestinationMobile from "$lib/assets/destination/background-destination-mobile.jpg";
	import bgCrewDesktop from "$lib/assets/crew/background-crew-desktop.jpg";
	import bgCrewTablet from "$lib/assets/crew/background-crew-tablet.jpg";
	import bgCrewMobile from "$lib/assets/crew/background-crew-mobile.jpg";
	import bgTechnologyDesktop from "$lib/assets/technology/background-technology-desktop.jpg";
	import bgTechnologyTablet from "$lib/assets/technology/background-technology-tablet.jpg";
	import bgTechnologyMobile from "$lib/assets/technology/background-technology-mobile.jpg";

	type Backgrounds = {
		[key: string]: {
			desktop: string;
			tablet: string;
			mobile: string;
		};
	};

	const backgrounds = {
		'/': {
			desktop: bgHomeDesktop,
			tablet: bgHomeTablet,
			mobile: bgHomeMobile
		},
		'/destination': {
			desktop: bgDestinationDesktop,
			tablet: bgDestinationTablet,
			mobile: bgDestinationMobile
		},
		'/crew': {
			desktop: bgCrewDesktop,
			tablet: bgCrewTablet,
			mobile: bgCrewMobile
		},
		'/technology': {
			desktop: bgTechnologyDesktop,
			tablet: bgTechnologyTablet,
			mobile: bgTechnologyMobile
		}
	} as Backgrounds;

	function currentBackground(path: string) {
		return backgrounds[path] || backgrounds['/'];
	}

	let { children } = $props();
</script>

<svelte:head><link rel="icon" href={favicon} /></svelte:head>

<div class="overflow-hidden">
<picture class="fixed min-h-screen min-w-screen z-[-1]">
	<source srcset={currentBackground(page.url.pathname).desktop} media="(min-width: 64rem)" />
	<source srcset={currentBackground(page.url.pathname).tablet} media="(min-width: 48rem)" />
	<img src={currentBackground(page.url.pathname).mobile} alt="Background" class="absolute inset-0 w-full h-full object-cover" />
</picture>
<header>
    <Navbar />
</header>

{@render children()}
</div>

