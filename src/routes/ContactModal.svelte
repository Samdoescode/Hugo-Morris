<script>
    // @ts-nocheck
    let dialog = $state();

    export function open() {
        dialog.showModal();
    }

    function onBackdropClick(e) {
        if (e.target === dialog) dialog.close();
    }
</script>

<!-- svelte-ignore a11y_no_noninteractive_element_interactions -->
<dialog
    bind:this={dialog}
    onclick={onBackdropClick}
    aria-labelledby="contact-heading"
>
    <div class="relative bg-zinc-900 text-zinc-100 rounded-lg p-8 w-full max-w-sm mx-auto">
        <button
            onclick={() => dialog.close()}
            aria-label="Close contact modal"
            class="absolute top-4 right-4 text-zinc-400 hover:text-zinc-100 transition-colors duration-200"
        >
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                <path stroke-linecap="round" stroke-linejoin="round" d="M6 18 18 6M6 6l12 12" />
            </svg>
        </button>

        <h2 id="contact-heading" class="gas text-3xl mb-6">Contact</h2>

        <p class="text-zinc-400 mb-2 text-sm">For enquiries, get in touch:</p>
        <a
            href="mailto:talent@sptm.com.au"
            class="text-lg text-rose-400 hover:text-rose-300 underline underline-offset-4 transition-colors duration-200 break-all"
        >
            talent@sptm.com.au
        </a>
    </div>
</dialog>

<style>
    dialog {
        background: transparent;
        border: none;
        padding: 1rem;
        width: 100%;
        max-width: 420px;
        margin: auto;
    }

    dialog::backdrop {
        background: rgba(0, 0, 0, 0.75);
        backdrop-filter: blur(4px);
    }
</style>
