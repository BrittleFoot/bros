<script lang="ts">
    export let name: string;
    export let broId: number;

    let asset = import(`./assets/${name}/avatar.png`)
</script>


<a href="/gallery?id={broId}" sveltekit:noscroll class="group cursor-pointer relative fade-in text-sm lg:-20 duration-300 z-20">
    <div class="w-full relative fade-in lg:group-hover:scale-105 group-hover:shadow-me duration-300 rounded-xl aspect-square aspect-w-1 aspect-h-1 overflow-hidden">
        <div class="w-full h-full bg-white opacity-0 absolute z-20"></div>
        <div class="animate-flash-once w-full h-full bg-white opacity-0 absolute z-20"></div>
        {#await asset then avatar}
            <img src={avatar.default} alt="Bro No. {broId}" class="duration-300 w-full h-full object-center object-cover absolute shadow-me"/>
        {:catch error}
            <p class='text-red-400'>{error.message}</p>
        {/await}
    </div>
    <p class="opacity-50  mt-3 uppercase font-mono tracking-widest text-3xs text-center">{name}</p>
    <h3 class="font-400  pb-2 -mt-1 text-2xs tracking-wider text-center uppercase">No. {broId}</h3>
</a>
