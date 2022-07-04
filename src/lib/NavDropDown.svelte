<script lang='ts'>
import { fly, fade } from "svelte/transition";

import ListDrop from "./ListDrop.svelte"
import NavItem from "./NavItem.svelte"

    export let links: { name: string, url: string } [] = []
    export let name: string

    export let dropped = false
    $: opacity = dropped ? 80 : 20

    const toggle = () => {
        dropped = !dropped
    }

</script>


<div class='relative'>
    <button class="nav-item flex items-center flex-row" on:click={toggle}>
        {name}<!----><ListDrop/>
    </button>

    {#if dropped}
    <div transition:fade class="fixed top-0 left-0 w-screen h-screen bg-black opacity-5" on:click={toggle}/>

    <div class='absolute flex flex-col space-y-2 right-0 top-10' on:click={toggle}>
        {#each links as link, i}
            <div class="ml-auto" in:fly={{y:-10, delay: i*100}} out:fly={{y:-10}}>
                <NavItem {...link} />
            </div>
        {/each}
    </div>
    {/if}
</div>

