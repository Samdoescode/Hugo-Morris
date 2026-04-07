<script>
    import bigtext from '$lib/images/headtext.png';
    import BGvid2 from '$lib/compressedHugoVid.mp4';
    import { onMount } from 'svelte';

    let videoReady = $state(false);

    onMount(() => {
        const timeout = setTimeout(() => (videoReady = true), 5000);
        return () => clearTimeout(timeout);
    });
</script>

<div class="loading-overlay" class:ready={videoReady} aria-hidden="true">
    <span class="gas loading-text">HUGO MORRIS</span>
</div>

<section aria-label="Hero" class="h-screen flex w-screen items-center justify-center">

    <video autoplay muted loop playsinline aria-hidden="true" class="absolute top-0 h-full w-full object-cover"
        oncanplaythrough={() => (videoReady = true)}>
        <source src={BGvid2} type="video/mp4" />
    </video>
    <video
        autoplay
        muted
        loop
        playsinline
        aria-hidden="true"
        class="invert absolute top-0 mix-blend-exclusion h-full w-full object-cover"
        style="mask-image: url({bigtext}); mask-size: contain; mask-repeat: no-repeat; mask-position: center;"
    >
        <source src={BGvid2} type="video/mp4" />
    </video>

</section>

<style>
    .loading-overlay {
        position: fixed;
        inset: 0;
        z-index: 50;
        background: #18181b;
        display: flex;
        align-items: center;
        justify-content: center;
        opacity: 1;
        pointer-events: all;
        transition: opacity 0.8s ease;
    }

    .loading-overlay.ready {
        opacity: 0;
        pointer-events: none;
    }

    .loading-text {
        font-size: clamp(1.5rem, 5vw, 3rem);
        color: white;
        letter-spacing: 0.2em;
        animation: pulse 2s ease-in-out infinite;
    }

    @keyframes pulse {
        0%, 100% { opacity: 1; }
        50% { opacity: 0.3; }
    }
</style>