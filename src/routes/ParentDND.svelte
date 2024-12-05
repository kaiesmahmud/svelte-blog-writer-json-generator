<script>
    import { flip } from "svelte/animate";
    import { dndzone } from "svelte-dnd-action";
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
</script>

<section
    class="bg-background"
    use:dndzone={{ items, flipDurationMs }}
    on:consider={handleDndConsider}
    on:finalize={handleDndFinalize}
>
    {#each items as item (item.id)}
        <div animate:flip={{ duration: flipDurationMs }} class="p-5 border rounded ">
            {#if item.name == "h1"}
                <h1>H1</h1>
            {:else if item.name == "h2"}
                <h2>H2</h2> 
            {:else if item.name == "h3"}
                <h3>H3</h3> 
            {:else if item.name == "h4"}
                <h4>H4</h4> 
            {:else if item.name == "h5"}
                <h5>H5</h5> 
            {:else if item.name == "h6"}
                <h6>H6</h6> 
            {:else if item.name == "p"}
                <p>Paragraph</p> 
            {:else if item.name == "img"}
                <p>img</p> 
            {:else if item.name == "list"}
                <p>list</p> 
            {:else}
                false component
            {/if}
            <!-- {item.name} -->
        </div>
    {/each}
</section>
