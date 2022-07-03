<script>
    import { beforeUpdate } from 'svelte';
    import { page } from '$app/stores'

    import GalleryGrid from "$lib/GalleryGrid.svelte";
    import BroDetailed from "$lib/BroDetailed.svelte";

    let queryBroId = parseInt($page.url.searchParams.get('id') ?? "");

    beforeUpdate(() => {
        queryBroId = parseInt($page.url.searchParams.get('id') ?? "")
    });
</script>


<div class="min-h-screen bg-white">
    <div>
        <main class="max-w-11xl mx-auto px-4 sm:px-6 lg:px-8">

            <div class="flex">
                <form class="hidden w-1/4 col-start-1 lg:block sticky top-0 h-screen pt-32">
                
                </form>

                <div class="lg:w-3/4 lg:px-8 w-full lg:pt-32 pt-28">
                    <div class="top-0 lg:bg-transparent left-0 px-4 pt-26 lg:pt-0 duration-300 lg:px-0 fixed w-full lg:relative z-10 flex items-end justify-between h-14  lg:pb-4 pb-3 border-b border-opacity-10 border-black bg-white">
                        <span class="w-full lg:py-1.5 sm:py-1 sm:px-1 lg:text-xl text-xs leading-5 font-extrabold lg:rounded-lg rounded-sm focus:outline-none hover:bg-white/[0.5] duration-300 bg-white">
                            Bros
                        </span>
                    </div>
                    <div class=" mb-">
                        <div class="lg:h-20 h-16 lg:pt-5 overflow-x-auto mx-auto hide-scrollbar flex items-center">
                            <h3 class="text-xs flex pr-2 items-center font-semibold uppercase tracking-wide opacity-50">
                                Full Collection
                            </h3>
                        </div>
                    </div>

                    <GalleryGrid/>
                </div>
            </div>
        </main>
    </div>

    {#if queryBroId} 
        <BroDetailed id={queryBroId}/>
    {/if}
</div>