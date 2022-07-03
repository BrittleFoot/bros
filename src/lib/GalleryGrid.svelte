<script>
import BroPane from "./BroPane.svelte";

</script>

<div class="grid lg:grid-cols-4 2xl:grid-cols-5 grid-cols-2 lg:gap-x-6 gap-x-4 lg:gap-y-2 gap-y-1  lg:col-span-3">
    {#each Array.from(Array(80).keys()) as i}
        <BroPane name="sis" broId={i+1}/>
    {/each}
</div>