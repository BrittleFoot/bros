<script type="ts">
    import EmblaCarousel from 'embla-carousel'
    import Autoplay from 'embla-carousel-autoplay';
    import { onMount,  } from 'svelte';

    let target: HTMLElement;

    onMount(() => {
        if (target) {    
            const embla = EmblaCarousel(target, {loop: true}, [Autoplay()])
            return () => embla.destroy()
        }
    })
</script>


<div bind:this={target} class="overflow-hidden">
    <div class="embla__container flex">
        <slot/>
    </div>
</div>