<script>
// @ts-nocheck
    import Headshot from '$lib/images/Headshot.jpeg';
    import Portfolio from './Portfolio.svelte';
    import { scale } from 'svelte/transition';
    import { quintOut } from 'svelte/easing';
	const wreaths = import.meta.glob(
		'$lib/images/wreaths/*.{avif,gif,heif,jpeg,jpg,png,tiff,webp}',
		{
			eager: true,
			query: {
				enhanced: true
			}
		}
	)
    let scroll;
</script>
<svelte:window bind:scrollY={scroll}
/>
<div class="w-full flex flex-row">
    <div class="w-1/3 z-10 shrink-0">
        <enhanced:img class="h-screen w-full object-cover sticky top-0" src={Headshot} alt="" />
    </div>

    <section class="w-4/5 flex flex-col">
        <div class="flex w-full min-h-screen justify-center flex-col p-4">
            <div  class=" flex-row -translate-x-24 z-10 rounded-lg bg-zinc-900 p-4 flex divide-x-2 divide-rose-800 gap-8" style:transform={`translate3d(0, ${(scroll - (scroll/2)) / 10}px, 0)`} >
                <div class="px-4">
                    <article class="container">
                        <p class=" max-w-prose py-2 text-lg/loose text-pretty text-zinc-100">
                            Hugo Morris is an emerging voice in the Sydney film scene. An award-winning writer and director with a speciality in genre films (westerns and noir specifically), Hugo’s style focuses on mastering the basics: the right look, the right sound, for the right story. No gimmicks. No bullshit.
        On set, Hugo is hands-on and precise, preferring to shape each scene in-camera as much as possible. No slow, expensive polish and fuss. Hugo keeps the work honest and grounded, creating real films and stories that stand out and stay with the audience long after the credits roll.
                        </p>
                    </article>
                 </div>
                <div class="shrink-0 flex h-4/5 w-1/3 flex-col gap-4">
                   
                    <div class="flex-1 min-h-0 grid h-3/5 grid-cols-3 gap-4 overflow-hidden">
                        {#each Object.entries(wreaths) as [_path, wreath]}
                            <div class="h-full w-full overflow-hidden">
                                <enhanced:img class="h-full w-full object-contain invert" src={wreath.default} alt="some alt text" />
                            </div>
                        {/each}
                    </div>

                </div>
            </div>
        </div>
    </section>
</div>