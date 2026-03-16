<script>
    import { videoHover } from '$lib/cursor-store';

    let played1 = $state(false);
    let played2 = $state(false);
    let played3 = $state(false);

    let iframe1 = $state(null);
    let iframe2 = $state(null);
    let iframe3 = $state(null);

    const id1 = 'upSuQjVlOC4';
    const id2 = 'kcSXC2oRJPc';
    const id3 = 'YbkASUEK9dE';

    // enablejsapi=1 allows postMessage control; no autoplay so it preloads silently
    const embedParams = '?controls=0&rel=0&color=white&iv_load_policy=3&enablejsapi=1';

    function thumb(id) {
        return `https://img.youtube.com/vi/${id}/maxresdefault.jpg`;
    }

    function embedSrc(id) {
        return `https://www.youtube.com/embed/${id}${embedParams}`;
    }

    function play(iframeEl, setPlayed) {
        setPlayed(true);
        iframeEl.contentWindow.postMessage(
            JSON.stringify({ event: 'command', func: 'playVideo', args: [] }),
            '*'
        );
    }
</script>

<section class="grow z-10 min-h-screen flex-col justify-center py-16 px-4 md:px-12">
    <div class="flex flex-col md:flex-row gap-6">
        <!-- Large video -->
        <div
            class="flex flex-col gap-2 md:flex-[2]"
            onmouseenter={() => videoHover.set(true)}
            onmouseleave={() => videoHover.set(false)}
        >
            <h2 class="gas text-zinc-100 text-2xl tracking-widest relative z-[53]">Showreel</h2>
            <div class="aspect-video relative z-[51]">
                <iframe
                    bind:this={iframe1}
                    src={embedSrc(id1)}
                    title="Hugo Morris — featured work"
                    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
                    allowfullscreen
                    class="w-full h-full rounded-lg"
                ></iframe>
                {#if !played1}
                    <div
                        class="absolute inset-0 z-[52] cursor-none rounded-lg bg-cover bg-center"
                        style="background-image: url('{thumb(id1)}')"
                        onclick={() => play(iframe1, (v) => (played1 = v))}
                        role="button"
                        tabindex="0"
                        onkeydown={(e) => e.key === 'Enter' && play(iframe1, (v) => (played1 = v))}
                        aria-label="Play video"
                    ></div>
                {/if}
            </div>
        </div>

        <!-- Two smaller videos stacked -->
        <div
            class="flex flex-col gap-2 md:flex-1"
            onmouseenter={() => videoHover.set(true)}
            onmouseleave={() => videoHover.set(false)}
        >
            <h2 class="gas text-zinc-100 text-2xl relative tracking-widest z-[53]">Commercials</h2>
            <div class="flex flex-col gap-6 flex-1">
                <div class="aspect-video flex-1 relative z-[51]">
                    <iframe
                        bind:this={iframe2}
                        src={embedSrc(id2)}
                        title="Hugo Morris — work sample 1"
                        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
                        allowfullscreen
                        class="w-full h-full rounded-lg"
                    ></iframe>
                    {#if !played2}
                        <div
                            class="absolute inset-0 z-[52] cursor-none rounded-lg bg-cover bg-center"
                            style="background-image: url('{thumb(id2)}')"
                            onclick={() => play(iframe2, (v) => (played2 = v))}
                            role="button"
                            tabindex="0"
                            onkeydown={(e) => e.key === 'Enter' && play(iframe2, (v) => (played2 = v))}
                            aria-label="Play video"
                        ></div>
                    {/if}
                </div>
                <div class="aspect-video flex-1 relative z-[51]">
                    <iframe
                        bind:this={iframe3}
                        src={embedSrc(id3)}
                        title="Hugo Morris — work sample 2"
                        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
                        allowfullscreen
                        class="w-full h-full rounded-lg"
                    ></iframe>
                    {#if !played3}
                        <div
                            class="absolute inset-0 z-[52] cursor-none rounded-lg bg-cover bg-center"
                            style="background-image: url('{thumb(id3)}')"
                            onclick={() => play(iframe3, (v) => (played3 = v))}
                            role="button"
                            tabindex="0"
                            onkeydown={(e) => e.key === 'Enter' && play(iframe3, (v) => (played3 = v))}
                            aria-label="Play video"
                        ></div>
                    {/if}
                </div>
            </div>
        </div>
    </div>
</section>
