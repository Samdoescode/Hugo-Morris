<script lang="ts">
  import MovieCards from './MovieCards.svelte';

</script>

<section id="portfolio" aria-hidden="true" class="min-h-screen w-full bg-rose-900 p-8 flex flex-col justify-center">
    
    <div class=" flex px-8 py-2">
        <ul class="flex flex-row shrink-0 tickerLeft w-[2200%] ticker gap-8">
            <MovieCards></MovieCards>
        </ul>  
        <ul aria-hidden="true" class="flex flex-row shrink-0 tickerLeft w-[2200%] ticker gap-8">
            <MovieCards></MovieCards>
        </ul>  
    </div>
    <div class=" flex px-8 py-2">
        <ul class="flex flex-row shrink-0 ticker w-[2200%] tickerRight gap-8">
            <MovieCards></MovieCards>
        </ul>  
        <ul aria-hidden="true" class="flex flex-row  shrink-0 tickerRight w-[2200%] ticker gap-8">
            <MovieCards></MovieCards>
        </ul>  
    </div>
    <div class=" flex px-8 py-2">
        <ul class="flex flex-row shrink-0 tickerLeft w-[2200%] -translate-x-1/2 ticker gap-8">
            <MovieCards></MovieCards>
        </ul>  
        <ul aria-hidden="true" class="flex flex-row shrink-0 -translate-x-1/2 tickerLeft w-[2200%] ticker gap-8">
            <MovieCards></MovieCards>
        </ul>  
    </div>
</section>