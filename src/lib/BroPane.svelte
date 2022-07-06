<script lang="ts">
    export let id: number;
    
    import { fade } from 'svelte/transition';

    let asset = import(`./assets/images/${id}.png`).then(m => m.default)

    const fadeOpts = {
        duration: 200,
        delay: id * 20
    }
</script>


<a href="/gallery?id={id}" sveltekit:noscroll in:fade={fadeOpts} out:fade={{duration:100}} class="group cursor-pointer relative fade-in text-sm lg:-20 z-20">
    <div class="w-full relative fade-in lg:group-hover:scale-105 duration-300 rounded-xl aspect-[0.78] overflow-hidden">
        <div class="w-full h-full bg-white opacity-0 absolute z-20"></div>

        <svg out:fade={{duration:50}} xmlns="http://www.w3.org/2000/svg" viewBox="0 0 780 1000" class="object-center object-fill animate-pulse absolute">
            <rect width="100%" height="100%" fill="#9c9"/>
        </svg>

        {#await asset then image}
            <img in:fade={{duration:50}} src={image} alt="Bro No. {id}" class="duration-300 w-full h-full object-center object-cover absolute"/>
        {:catch error}
            <p class='text-red-400'>{error.message}</p>
        {/await}
    </div>
    <p class="opacity-50  mt-3 uppercase font-mono tracking-widest text-3xs text-center">Bros</p>
    <h3 class="font-400  pb-2 -mt-1 text-2xs tracking-wider text-center uppercase">No. {id}</h3>
</a>
