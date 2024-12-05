<script>
    import * as Tabs from "$lib/components/ui/tabs";
    import AspectRatio from "@/components/ui/aspect-ratio/aspect-ratio.svelte";

    export let dndResult
</script>

<div class="col-span-6 border rounded p-5">
    <Tabs.Root value="blog" class=" ">
        <Tabs.List>
            <Tabs.Trigger value="blog" class="font-bold">Blog</Tabs.Trigger>
            <Tabs.Trigger value="json" class="font-bold">Json Code</Tabs.Trigger
            >
        </Tabs.List>
        <Tabs.Content value="blog" class="w-full border p-5">
            {#each $dndResult as item}
                {#if item.data.type === "h1"}
                    <h1 
                    itemprop="headline" 
                    aria-label="Article headline"
                    title={item.data.value}
                    >
                        {@html item.data.value}
                    </h1>
                {:else if item.data.type === "h2"}
                    <h2 
                    aria-label="Section heading"
                    title={item.data.value}
                    >
                        {@html item.data.value}
                    </h2>
                {:else if item.data.type === "h3"}
                    <h3 aria-label="Subsection heading" title={item.data.value}>
                        {@html item.data.value}
                    </h3>
                {:else if item.data.type === "h4"}
                    <h4 aria-label="Sub-subsection heading" title={item.data.value}>
                        {@html item.data.value}
                    </h4>
                {:else if item.data.type === "h5"}
                    <h5 aria-label="Minor heading" title={item.data.value}>
                        {@html item.data.value}
                    </h5>
                {:else if item.data.type === "h6"}
                    <h6 aria-label="Minor heading" title={item.data.value}>
                        {@html item.data.value}
                    </h6>
                {:else if item.data.type === "p"}
                    <p itemprop="articleBody" aria-label="Article content" title={item.data.value}>
                        {@html item.data.value}
                    </p>
                {:else if item.data.type === "img"}
                    <figure
                        itemprop="image"
                        itemscope
                        itemtype="https://schema.org/ImageObject"
                    >
                        <AspectRatio
                            ratio={4 / 3}
                            class="p-0 rounded-lg overflow-hidden"
                        >
                            <img
                                src={item.data.src}
                                alt={item.data.alt}
                                class="rounded-md object-cover"
                                loading="lazy"
                                intrinsicsize="450 x 300"
                            />
                        </AspectRatio>
                        {#if item.data.caption}
                            <figcaption itemprop="caption">
                                {item.data.caption}
                            </figcaption>
                        {/if}
                    </figure>
                {/if}
            {/each}
        </Tabs.Content>
        <Tabs.Content value="json" class="w-full border p-5"
            >Change your password here.</Tabs.Content
        >
    </Tabs.Root>
</div>

<style lang="postcss">
    h1 {
        @apply text-4xl font-bold text-gray-900 mb-6 leading-tight;
    }

    h2 {
        @apply text-3xl font-bold text-gray-800 mb-4 leading-tight;
    }

    h3 {
        @apply text-2xl font-semibold text-gray-800 mb-4;
    }

    h4 {
        @apply text-xl font-semibold text-gray-800 mb-3;
    }

    h5 {
        @apply text-lg font-semibold text-gray-800 mb-3;
    }

    h6 {
        @apply text-base font-semibold text-gray-800 mb-3;
    }

    p {
        @apply text-[18px] lg:text-[20px] text-gray-700 leading-relaxed mb-4 text-justify;
    }

    img {
        @apply w-full h-auto rounded-lg shadow-md my-6;
    }
    a {
        @apply underline hover:text-blue-500 font-medium text-sky-800 !important;
    }
    .p-a {
        @apply underline hover:text-blue-500 font-medium text-sky-800;
    }
</style>
