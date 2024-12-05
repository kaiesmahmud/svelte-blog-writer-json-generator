<script>
    import { flip } from "svelte/animate";
    import { dndzone } from "svelte-dnd-action";
    import H1Dnd from "@/components/dnd-components/H1-dnd.svelte";
    // @ts-ignore
    export let dndResult, items;

    const flipDurationMs = 300;
    function handleDndConsider(e) {
        items = e.detail.items;
    }
    function handleDndFinalize(e) {
        items = e.detail.items;
        dndResult.update(() => items);
    }

    // js file example
    // "content": [
    //   {
    //     "type": "h1",
    //     "value": "Top 7 Places To See The Northern Lights in 2025 in Europe"
    //   },
    //   {
    //     "type": "p",
    //     "value": "Picture yourself beneath a star-studded Arctic sky as waves of green, purple, and pink lights dance overhead. The Northern Lights, or Aurora Borealis, are nature's most stunning show. They draw thousands of travelers to northern Europe each year. As we approach 2025, scientists predict exceptional aurora activity during the solar maximum period, making it the perfect time to plan your Northern Lights adventure.From Finland's cozy glass igloos to Norway's dramatic fjords, Europe offers some of the world's most spectacular venues for witnessing this celestial phenomenon. The key is knowing exactly where to go—locations that combine pristine dark skies with unforgettable Arctic experiences. We've handpicked seven destinations where your chances of catching this magical display are highest, each offering its own unique way to experience the aurora's ethereal dance."
    //   },
    //   {
    //     "type": "img",
    //     "src": "https://i.ibb.co.com/71kWsdW/troms-norway.webp",
    //     "alt": "Tromsø, Norway"
    //   },
    //   {
    //     "type": "h2",
    //     "value": "1. Tromsø, Norway"
    //   },
    //   {
    //     "type": "h2",
    //     "value": "4. Abisko, Sweden"
    //   },
    //   {
    //     "type": "h3",
    //     "value": "Tips for Viewing"
    //   },
    // ],
</script>

<section
    class="bg-background"
    use:dndzone={{ items, flipDurationMs }}
    on:consider={handleDndConsider}
    on:finalize={handleDndFinalize}
>
    {#each items as item (item.id)}
        <div
            animate:flip={{ duration: flipDurationMs }}
            class="p-1 border rounded flex gap-1 items-center"
        >
            {#if item.name == "h1"}
                <H1Dnd {item} {dndResult} />
            {:else if item.name == "h2"}
                <H1Dnd {item} {dndResult} />
            {:else if item.name == "h3"}
                <H1Dnd {item} {dndResult} />
            {:else if item.name == "h4"}
                <H1Dnd {item} {dndResult} />
            {:else if item.name == "h5"}
                <H1Dnd {item} {dndResult} />
            {:else if item.name == "h6"}
                <H1Dnd {item} {dndResult} />
            {:else if item.name == "p"}
                <p>Paragraph</p>
            {:else if item.name == "img"}
                <p>img</p>
            {:else if item.name == "list"}
                <p>list</p>
            {:else}
                false component
            {/if}
        </div>
    {/each}
</section>
