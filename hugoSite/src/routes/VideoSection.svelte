<script>
    import bigtext from '$lib/images/headtext.png';
    import bgvideov2 from '$lib/bgvideov2.mov';
</script>


<section class=" h-screen w-screen content-center">
    
    <video autoplay muted loop class=" absolute top-0 h-full w-full object-cover">
        <source src={bgvideov2} type="video/mp4" />
    </video>
    <video autoplay muted loop class="invert absolute top-0 mix-blend-exclusion mask-[url($lib/images/headtext.png)] mask-contain mask-no-repeat bg-blend-multiply mask-center h-full w-full object-cover">
        <source src={bgvideov2} type="video/mp4" />
    </video>
</section>