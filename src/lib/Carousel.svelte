<script type="ts">
    import EmblaCarousel, { type EmblaCarouselType } from 'embla-carousel'
    import Autoplay from 'embla-carousel-autoplay';
    import { beforeUpdate, onMount,  } from 'svelte';

    let target: HTMLElement;

    let embla: EmblaCarouselType;

    $: console.log($$slots)

    onMount(() => {
        if (target) {    
            embla = EmblaCarousel(target, {loop: true}, [Autoplay()])
            return () => embla.destroy()
        }
    })
</script>


<div bind:this={target} class="overflow-hidden">
    <div class="embla__container flex">
        <slot name="slides"/>
    </div>
</div>