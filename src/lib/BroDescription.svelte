<script type="ts">
    export let avatar: string;
    export let text: string;
</script>

<div class="mb-3 pb-3">
    <div class="grid grid-cols-9 gap-x-4 mt-3">
        <img src={avatar} alt="Bro's avatar" class="col-start-3 col-span-5 md:col-start-4 md:col-span-3" />
    </div>
    <p class="font-mono text-justify mb-3 mt-1 px-4">
        {text}
    </p>
</div>