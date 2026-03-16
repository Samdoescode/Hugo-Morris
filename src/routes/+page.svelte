<script lang="ts">
	import AboutSection from './AboutSection.svelte';
	import WorkSection from './WorkSection.svelte';
	import Portfolio from './Portfolio.svelte';
	import VideoSection from './VideoSection.svelte';
</script>

<svelte:head>
	<title>Hugo Morris</title>
	<meta name="description" content="Hugo Morris — Sydney-based film director and writer." />
</svelte:head>

<section>
	<VideoSection />
	<AboutSection />
	<div class="relative min-h-screen overflow-hidden">
		<div class="absolute inset-0">
			<Portfolio />
		</div>
		<WorkSection />
	</div>
</section>


