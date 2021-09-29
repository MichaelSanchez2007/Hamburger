2<script>
    let alienY, alienX;
    let alienW, alienH;

    export let hovering;

    function showMe(e) {
        alienX = e.clientX - alienW /2
        alienY = e.clientY - alienH /2
    }
</script>

<svelte:window on:mousemove={showMe} />

<h1
    style="transform: translate({alienX}px, {alienY}px) scale({hovering ? '10' : '1'})"
    bind:clientHeight={alienH}
    bind:clientWidth={alienW}
>
</h1>

<style>
    h1 {
        background-image: url(https://creators-images.vice.com/content-images/contentimage/no-slug/35f297d210dac499db94bbdfd19e6c04.jpg?resize=640:*);
        position: absolute;
        width: 100px;
        height: 100px;
        cursor: none;
        user-select: none;
        pointer-events: none;
        background-size: contain;
        border-radius: 25px;
    }
</style>