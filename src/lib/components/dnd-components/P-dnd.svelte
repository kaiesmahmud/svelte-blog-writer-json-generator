<script>
    import { Textarea } from "$lib/components/ui/textarea";
    export let item, dndResult;

    const onChange = (e) => {
        dndResult.update((items) => {
            return items.map((i) =>
                i.id === item.id
                    ? { ...i, data: { ...i.data, value: e.target.value } }
                    : i,
            );
        });
    };
</script>

<span class="text-xl cursor-grab">
    <svg
        xmlns="http://www.w3.org/2000/svg"
        width="1em"
        height="1em"
        viewBox="0 0 16 16"
        {...$$props}
    >
        <g
            fill="none"
            stroke="currentColor"
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="1.5"
        >
            <circle cx="5.5" cy="2.5" r=".75" />
            <circle cx="5.5" cy="8" r=".75" />
            <circle cx="5.5" cy="13.5" r=".75" />
            <circle cx="10.496" cy="2.5" r=".75" />
            <circle cx="10.496" cy="8" r=".75" />
            <circle cx="10.496" cy="13.5" r=".75" />
        </g>
    </svg>
</span>
<div class="w-full">
    <span class=" uppercase font-bold p-1">{item.name}</span>
    <Textarea
        variant="outline"
        placeholder="H1 content here"
        type="search"
        value={item.data.value}
        on:input={onChange}
    />
</div>
