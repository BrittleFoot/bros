<script type="ts">
    export let image: string;
    export let text: string;
</script>

<div class="mb-3 pb-3 ml-6 mt-6 grid grid-cols-1 mr-6 md:mr-0">
    <img src={image} alt="Bro's avatar" class="rounded-xl" />
    <p class="font-mono text-center mt-3">
        {text}
    </p>
</div>