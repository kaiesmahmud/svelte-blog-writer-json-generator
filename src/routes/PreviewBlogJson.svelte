<script>
    import * as Tabs from "$lib/components/ui/tabs";
</script>

<div class="col-span-6 border rounded p-5"> 
    <Tabs.Root value="blog" class=" ">
        <Tabs.List >
            <Tabs.Trigger value="blog" class="font-bold">Blog</Tabs.Trigger>
            <Tabs.Trigger value="json" class="font-bold">Json Code</Tabs.Trigger>
        </Tabs.List>
        <Tabs.Content value="blog" class="w-full border p-5">
            Make changes to your account here.
        </Tabs.Content>
        <Tabs.Content value="json" class="w-full border p-5">Change your password here.</Tabs.Content>
    </Tabs.Root>
</div>
