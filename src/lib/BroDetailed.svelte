<script type='ts'>
    export let id: number;

    import { fly, fade } from 'svelte/transition';
    import { circOut } from 'svelte/easing';
    import { goto } from '$app/navigation';
    
    import BroProperty from './BroProperty.svelte';
    
    import BroDescription from './BroDescription.svelte';
    import Carousel from './Carousel.svelte';

    import preview from '$lib/assets/preview.gif'
    import { onMount } from 'svelte';
    
    const goToGalery = () => goto('/gallery', {noscroll: true})

    interface BroMeta {
        name: string,
        description: string,
        attributes: {
            trait_type: string,
            value: string
        }[]
    }

    let image: string;
    let meta: BroMeta;
    $: properties = meta?.attributes ?? []


    onMount(async () => {
        const metaModule = await import(`./assets/json/${id}.json`)
        const imageModule = await import(`./assets/images/${id}.png`)

        image = imageModule.default;
        meta = metaModule.default;
    });


</script>



<div transition:fade on:mousedown|self={goToGalery} class='fixed top-0 left-0 bg-opacity-90 w-screen h-screen z-40 opacity-100 bg-white'>

    {#if meta}
    <div in:fly={{y:100}} out:fly={{y: 100, easing: circOut}} class="fixed left-1/2 top-1/2 translate-y-[-50%] translate-x-[-50%] w-11/12 max-w-3xl min-h-[25%] bg-gray-200 shadow-xl rounded-3xl">

        <button on:click={goToGalery} class="absolute top-4 right-4 z-[60] h-6 w-6 opacity-50 md:hidden">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" class="fill-current">
                <line x1="0" y1="0" x2="100%" y2="100%" stroke="black" stroke-width="2"/>
                <line x1="0" y1="100%" x2="100%" y2="0" stroke="black" stroke-width="2"/>
            </svg>
        </button>

        <div class="grid md:grid-cols-12 grid-cols-1 gap-x-10 mx-auto z-50 sm:max-w-xl md:max-w-fit max-h-fit">

            <div class="col-span-6 flex">
                <BroDescription image={image} text={meta.description}/>
            </div>

            <div class="h-full relative col-span-6 md:pr-10 md:pl-0 px-6 md:py-0 py-6 flex-col w-full flex justify-top">

                <div class="border-opacity-10 flex space-between items-end w-full border-bb border-black sm:pt-3 md:pt-6">
                    <div class="overflow-hidden text-left pl-4 pt-3 bg-black bg-opacity-10 pb-2 rounded w-full border-opacity-0 border-white">
                        <span class="font-mono text-2xl">{meta.name}</span>
                    </div>
                </div>

                <div class="grid grid-cols-1">
                    <div class="overlay-item flex flex-col">
                        <ul class="pt-2 mt-6 max-w-xl grid grid-cols-1 gap-3 mb-4 my">
                            {#each properties as {trait_type, value}}
                            <li>
                                <BroProperty name={trait_type} value={value} icon="@"/>
                            </li>
                            {/each}
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </div>
    {/if}

</div>
