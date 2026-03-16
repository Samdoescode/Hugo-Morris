<script>
    import bigtext from '$lib/images/headtext.png';
    import BGvid2 from '$lib/compressedHugoVid.mp4';
</script>


<section class=" h-screen flex w-screen content-center items-center justify-center">
    

    <video autoplay muted loop class="absolute top-0 h-full w-full object-cover">
        <source src={BGvid2} type="video/mp4" />
    </video>
    <video
        autoplay
        muted
        loop
        class="invert absolute top-0 mix-blend-exclusion h-full w-full object-cover"
        style="mask-image: url({bigtext}); mask-size: contain; mask-repeat: no-repeat; mask-position: center;"
    >
        <source src={BGvid2} type="video/mp4" />
    </video>

</section>