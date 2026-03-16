<script>
// @ts-nocheck
    import Headshot from '$lib/images/Headshot.jpeg';
    import ContactModal from './ContactModal.svelte';
    let modalRef = $state();
	const wreaths = import.meta.glob(
		'$lib/images/wreaths/*.{avif,gif,heif,jpeg,jpg,png,tiff,webp}',
		{
			eager: true,
			query: {
				enhanced: true
			}
		}
	)
    let scroll = 0;
</script>
<svelte:window bind:scrollY={scroll}
/>
<div class="w-full flex flex-col md:flex-row">
    <div class="w-full md:w-1/3 z-10 md:shrink-0">
        <enhanced:img class="h-[50vh] md:h-screen w-full object-cover md:sticky md:top-0" src={Headshot} alt="Hugo Morris" />
    </div>

    <section aria-label="About" class="w-full md:w-4/5 flex flex-col">
        <div class="flex w-full min-h-screen justify-center flex-col p-4">
            <div  class=" flex-col md:flex-row translate-x-0 md:-translate-x-24 z-10 rounded-lg bg-zinc-900 p-4 flex divide-y-2 md:divide-y-0 md:divide-x-2 divide-rose-800 gap-8" style:transform={`translate3d(0, ${scroll / 20}px, 0)`} >
                <div class="px-4">
                    <article class="container">
                        <p class=" max-w-prose py-2 text-lg/loose text-pretty text-zinc-100">
                            Hugo Morris is a Sydney-based commercial director with a sharp, cinematic eye and a taste for bold choices. With a background in fine art painting, Hugo brings a strong visual signature to every frame: sculpted light, deliberate composition, charged performances. Brutal when it should be. Always grounded in story.
If you’re ready to make work that feels distinctive, confident, and unmistakably authored, let’s create something bold.
                        </p>
                    </article>
                    <div class="flex relative bottom-0  text-center w-full flex-row group justify-between pr-2 pt-4">

                        <button type="button" onclick={() => modalRef.open()} class="px-4 flex flex-row gap-2 transition-all duration-200 hover:border-zinc-600 hover:bg-zinc-400 hover:shadow-xl  bg-opacity-60 dark:bg-opacity-40 grow text-left rounded-l-lg bg-zinc-300 p-3">
                            <p>Work with me</p>
                            <svg aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                                stroke="currentColor" class="w-6 h-6">
                                <path stroke-linecap="round" stroke-linejoin="round"
                                    d="M17.25 8.25L21 12m0 0l-3.75 3.75M21 12H3" />
                            </svg>
                        </button>
                        <a href="#portfolio" class="px-4 rounded-r-lg p-3 group bg-zinc-400 flex flex-row gap-2 transition-all duration-200 hover:border-zinc-700 hover:bg-rose-800 hover:shadow-xl hover:grow bg-opacity-60">
                            <p>See my work</p>
                            <svg aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6 transition-all duration-200 opacity-0 group-hover:opacity-100">
  <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 13.5 12 21m0 0-7.5-7.5M12 21V3" />
</svg>

                        </a>
                    </div>
                 </div>
                <div class="w-full md:w-1/3 md:h-4/5 md:shrink-0 flex flex-col gap-4">

                    <div class="flex-1 min-h-0 grid h-auto md:h-3/5 grid-cols-2 md:grid-cols-3 gap-4 overflow-hidden">
                        {#each Object.entries(wreaths) as [_path, wreath]}
                            <div class="h-full w-full overflow-hidden">
                                <enhanced:img class="h-full w-full object-contain invert" src={wreath.default} alt="Film festival laurel" />
                            </div>
                        {/each}
                    </div>

                </div>
            </div>
        </div>
    </section>
</div>

<ContactModal bind:this={modalRef} />