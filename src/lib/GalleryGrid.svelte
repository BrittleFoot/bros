<script>
import BroPane from "./BroPane.svelte";

</script>

<div class="grid grid-cols-2 md:grid-cols-4 lg:grid-cols-4 2xl:grid-cols-5  lg:gap-x-6 gap-x-4 lg:gap-y-2 gap-y-1  lg:col-span-3">
    {#each Array.from(Array(10).keys()) as i}
        <BroPane id={i+1}/>
    {/each}
</div>