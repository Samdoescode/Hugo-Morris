<script>
    // @ts-nocheck
	import { Spring } from 'svelte/motion';

	let coordsWide = new Spring({ x: 50, y: 50 }, {
		stiffness: 0.05,
		damping: 0.25
	});
    let coordsInner = new Spring({ x: 50, y: 50 }, {
		stiffness: 0.1,
		damping: 0.35
	});
	let size = new Spring(10);
    let scroll = 0;
    let lastMouseX = 50;
    let lastMouseY = 50;
    
</script>

<svelte:window bind:scrollY={scroll}
	onmousemove={(e) => {
		lastMouseX = e.clientX;
		lastMouseY = e.clientY;
		coordsWide.target = { x: e.clientX, y: e.clientY };
        coordsInner.target = { x: e.clientX, y: e.clientY };
	}}
	onmousedown={() => (size.target = 30)}
	onmouseup={() => (size.target = 10)}
/>

<div class="w-screen h-screen fixed top-0 left-0 pointer-events-none z-50">
    <svg class="w-full h-full"
        role="presentation"
        >
        <circle cx={coordsWide.current.x} cy={coordsWide.current.y} r={size.current} stroke="lightgray" stroke-width="1" fill-opacity="0"/>
        <circle cx={coordsInner.current.x} cy={coordsInner.current.y} r={size.current/4} fill="darkgray"/>
    </svg>
</div>



<style>
	:global(body) {
		cursor: none;
	}
	
	svg {
		position: absolute;
		top: 0;
		left: 0;
		pointer-events: none;
	}
</style>