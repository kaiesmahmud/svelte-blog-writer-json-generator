<script>
	import { Button } from "@/components/ui/button";
	import PreviewBlogJson from "./PreviewBlogJson.svelte";

	const allButtons = ["h1", "h2", "h3", "h4", "h5", "h6", "p", "img", "list"];

	import { writable } from "svelte/store";
	import ParentDnd from "./ParentDND.svelte";

	let nodes = [
		{ id: 1, name: "h1", data: { type: "h1", value: "some data" } },
	];
	let dndResult = writable(nodes);

	const addNewItem = (/** @type {any} */ name) => {
		//generate id
		// @ts-ignore
		let items = $dndResult;
		let id = items.length + 1;
		// check id
		// @ts-ignore
		if (!$dndResult[id]) {
			//Add New Page to Main Obj
			// @ts-ignore
			items = [...items, { id, name, data: { type: name, value: "" } }];
			// @ts-ignore
		} else {
			// @ts-ignore
			alert("Duplicate  id !");
		}

		// @ts-ignore
		dndResult.update(() => items);
		// @ts-ignore
	};

	dndResult.subscribe((va) => console.log(" update ", va));
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section class="w-full min-h-screen grid grid-cols-12 border gap-5 p-5">
	<div class="flex flex-col gap-2 p-3">
		{#each allButtons as item}
			<Button
				on:click={() => addNewItem(item)}
				variant="outline"
				class="flex gap-3 font-bold  p-5"
				title={item}
			>
				<span class="text-xl text-slate-700">
					<svg
						xmlns="http://www.w3.org/2000/svg"
						width="1em"
						height="1em"
						viewBox="0 0 24 24"
						{...$$props}
					>
						<path
							fill="currentColor"
							d="M11 13H5v-2h6V5h2v6h6v2h-6v6h-2z"
						/>
					</svg>
				</span>
				<span class=" uppercase">
					{item}
				</span>
			</Button>
		{/each}
	</div>
	<div class="col-span-5 border rounded p-5 bg-muted/50 space-y-2">
		<h1 class="text-xl font-bold">Blog Page Create</h1>
		<ParentDnd {dndResult} items={$dndResult} />
	</div>
	<PreviewBlogJson {dndResult} />
</section>
