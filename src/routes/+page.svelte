<script>
    import {Button} from "@/components/ui/button";


	const allButtons = [
		"h1",
		"h2",
		"h3",
		"h4",
		"h5",
		"h6",
		"p",
		"img",
		"list",
	]
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section class="w-full min-h-screen grid grid-cols-12 border gap-5 p-5">
	 <div class="flex flex-col gap-2 p-3">
		{#each allButtons as item}
			<Button variant="outline" class="flex gap-3 font-bold  p-5" title={item}>
				<span class="text-xl text-slate-700">
					<svg xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 24 24" {...$$props}>
						<path fill="currentColor" d="M11 13H5v-2h6V5h2v6h6v2h-6v6h-2z" />
					</svg>
				</span>
				<span class=" uppercase">
					{item}
				</span>
			</Button>
		{/each}
	 </div>
	 <div class="col-span-5 border rounded p-5 bg-muted/50">
		<h1 class="text-xl font-bold">DND</h1>
	</div>
	<div class="col-span-6 border rounded p-5">
		<h1 class="text-xl font-bold">Blog</h1>
		
	 </div>
	
</section>
 
