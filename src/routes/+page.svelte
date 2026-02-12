<script lang="ts">
	import AboutSection from './AboutSection.svelte';
	import Mousecursor from './Mousecursor.svelte';
	import Portfolio from './Portfolio.svelte';
	import VideoSection from './VideoSection.svelte';
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section class="relitive">
	<VideoSection />
	<AboutSection />
	<Portfolio />
</section>


