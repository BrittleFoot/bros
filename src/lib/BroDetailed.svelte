<script type='ts'>
    import { fly, fade } from 'svelte/transition';
    import { goto } from '$app/navigation';
    export let id: number;
    
    import avatar from '$lib/assets/sis/avatar.png'
    import full from '$lib/assets/sis/full.png'
    import BroProperty from './BroProperty.svelte';
    
    const goToGalery = () => goto('/gallery', {noscroll: true})
    
    import EmblaCarousel from 'embla-carousel'
    import type {EmblaCarouselType} from 'embla-carousel'
	import Autoplay from 'embla-carousel-autoplay';
    import { beforeUpdate,  } from 'svelte';
import { circIn, circOut } from 'svelte/easing';

    const flyOpts = {
        y: 100,
    }

    const flyOutOpts = {
        y: 100,
        easing: circOut
    }

    let embla : EmblaCarouselType;

    beforeUpdate(() => {
        if (embla) {
            embla.destroy();
        }
        const emblaNode = document.querySelector<HTMLElement>('.embla')
        const options = { loop: true }

        if (emblaNode) {
            embla = EmblaCarousel(emblaNode, options, [Autoplay()])
        }
    })

</script>



<div transition:fade on:click|self={goToGalery} class='fixed top-0 left-0 bg-opacity-90 w-screen h-screen z-40 opacity-100 bg-white'>
    <div in:fly={flyOpts} out:fly={flyOutOpts} class="fixed left-1/2 top-1/2 translate-y-[-50%] translate-x-[-50%] w-11/12 max-w-6xl min-h-[25%] bg-gray-200 shadow-xl rounded-3xl">

        <div class="grid md:grid-cols-12 grid-cols-1 gap-x-10 mx-auto z-50 sm:max-w-xl md:max-w-fit">
            <div class="col-span-6">
                <img src={full} alt="Bro in full straight position"/>
            </div>

            <div class="h-full relative col-span-6 md:pr-10 md:pl-0 px-6 md:py-0 py-6 flex-col w-full flex justify-top">

                <div class="border-opacity-10 flex space-between items-end w-full border-bb border-black sm:pt-3 md:pt-6">
                    <div class="overflow-hidden text-left pl-4 pt-3 bg-black bg-opacity-10 pb-2 rounded w-full border-opacity-0 border-white">
                        <span class="font-mono text-2xl">Bro #{id}</span>
                    </div>
                </div>

                <div class="grid grid-cols-1">
                    <div class="overlay-item flex flex-col">
                        <ul class="pt-2 mt-6 max-w-xl lg:grid-cols-2 gap-3 lg:grid hidden">
                            {#each [1,2,3,4,5,6,7,8,9] as i}
                            <li>
                                <BroProperty name="Style" value="Impressive" icon="@"/>
                            </li>
                            {/each}
                        </ul>

                        <div class="embla lg:hidden">
                            <div class="pt-2 mt-3 max-w-xl lg:hidden space-x-2 embla__container">
                                {#each [1,2,3,4,5,6,7,8,9] as i}
                                <div class="embla__slide">
                                    <BroProperty name="Style" value="Impressive" icon="@"/>
                                </div>
                                {/each}
                            </div>
                        </div>
                    </div>
                </div>

                <div class="hidden md:block lg:block">
                    <div class="grid grid-cols-9 gap-x-4 mt-3">
                        <img src={avatar} alt="Bro's avatar" class=" col-start-4 col-span-3" />
                    </div>
                    <p class="font-mono text-justify">
                        Lorem ipsum dolor sit amet consectetur, adipisicing elit. 
                        Est incidunt, voluptatibus laudantium ipsam veritatis nostrum! 
                        Repellendus pariatur veritatis expedita, unde at sequi. 
                        Provident harum ducimus ipsam deleniti! At, qui porro.
                    </p>
                </div>


            </div>
        </div>
    </div>

</div>


<style>
    .embla {
       overflow: hidden;
    }
    .embla__container {
        display: flex;
    }
    .embla__slide {
        position: relative;
        flex: 0 0 100%;
    }
</style>