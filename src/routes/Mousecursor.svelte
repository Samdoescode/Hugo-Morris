<script>
    // @ts-nocheck
	import { Spring } from 'svelte/motion';
    import { videoHover } from '$lib/cursor-store';

	let coordsWide = new Spring({ x: 50, y: 50 }, {
		stiffness: 0.05,
		damping: 0.25
	});
    let coordsInner = new Spring({ x: 50, y: 50 }, {
		stiffness: 0.1,
		damping: 0.35
	});
	let size = new Spring(10);

    let hovering = $state(false);
    videoHover.subscribe(v => { hovering = v; });

    $effect(() => {
        size.target = hovering ? 48 : 10;
    });
</script>

<svelte:window
	onmousemove={(e) => {
		coordsWide.target = { x: e.clientX, y: e.clientY };
        coordsInner.target = { x: e.clientX, y: e.clientY };
	}}
	onmousedown={() => (size.target = 30)}
	onmouseup={() => (size.target = hovering ? 48 : 10)}
/>

<div class="cursor-wrapper w-screen h-screen fixed top-0 left-0 pointer-events-none z-[60]">
    <svg class="w-full h-full"
        role="presentation"
        >
        <circle
            cx={coordsWide.current.x}
            cy={coordsWide.current.y}
            r={size.current}
            stroke={hovering ? 'white' : 'lightgray'}
            stroke-width="1"
            fill-opacity="0"
        />
        <circle
            cx={coordsInner.current.x}
            cy={coordsInner.current.y}
            r={size.current / 4}
            fill={hovering ? 'none' : 'darkgray'}
            stroke={hovering ? 'white' : 'none'}
            stroke-width={hovering ? '1.5' : '0'}
        />
    </svg>
</div>



<style>
	svg {
		position: absolute;
		top: 0;
		left: 0;
		pointer-events: none;
	}

	@media (hover: none) {
		.cursor-wrapper {
			display: none;
		}
	}
</style>
