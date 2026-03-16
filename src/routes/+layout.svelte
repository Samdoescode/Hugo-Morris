<script lang="ts">
	import './layout.css';
	import Mousecursor from './Mousecursor.svelte';
	let { children } = $props();
</script>

<div class="bg-zinc-900 overflow-x-clip">
	<main>{@render children()}</main>
	<Mousecursor />
</div>

