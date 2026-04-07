<script lang="ts">
	import './layout.css';
	import Mousecursor from './Mousecursor.svelte';
	let { children } = $props();
	import { dev } from '$app/environment';
	import { injectAnalytics } from '@vercel/analytics/sveltekit';
	import { injectSpeedInsights } from '@vercel/speed-insights/sveltekit';
	injectSpeedInsights();
	injectAnalytics({ mode: dev ? 'development' : 'production' });
</script>

<div class="bg-zinc-900 overflow-x-clip">
	<main>{@render children()}</main>
	<Mousecursor />
</div>

