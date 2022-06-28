<script lang='ts'>
import ListDrop from "./ListDrop.svelte"

    export let urls: string[] = []
    export let name: string

    export let dropped = false
    $: opacity = dropped ? 80 : 20

</script>


<div class='relative'>
    <button class="nav-item flex items-center flex-row" on:click={() => dropped = !dropped}>
        {name}<!----><ListDrop/>
    </button>

    {#if dropped}
    <div class='absolute flex flex-col space-y-2 right-0 top-10'>
        {#each urls as url}
            <a class='nav-item' href={url}>{url}</a>
        {/each}
    </div>
    {/if}
</div>

