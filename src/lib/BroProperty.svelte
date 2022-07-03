<script type='ts'>
    export let icon: string;
    export let name: string;
    export let value: string;
</script>


<div class="text-xs items-center py-2 px-3 flex rounded bg-gray-500 bg-opacity-10 w-full border-black">
    <span class="pr-2 font-mono text-2xl">{icon}</span>
    <div>
        <p class="items-center uppercase opacity-60 font-mono text-2xs tracking-wider mr-auto inline-block"><span>{name}</span><span>:</span></p>
        <p class="ml-auto text-xs font-600 uppercase bold">{value}</p>
    </div>
</div>