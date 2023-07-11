<script lang="ts">
	import { createPopover } from '@melt-ui/svelte';
	import { fade } from 'svelte/transition';

	const { trigger, content, open, arrow, close } = createPopover();
	// $arrow.style = "position:absolute;width:var(--arrow-size, 12px);height:var(--arrow-size, 12px);"


	export let popoverInfoHTML = {
		head: `ListItemTop from PopInfo`,
		body: `<div class="bg-neutral-200 p-2 text-left">Lorem ipsum dolor sit amet consectetur adipisicing elit. Porro illum at similique iure aut, quis blanditiis, exercitationem maiores accusamus cupiditate recusandae quo magni sunt ipsum sequi? Eaque illum excepturi suscipit!
Cupiditate esse quo nesciunt dolores repudiandae soluta a impedit odio, ducimus ab nobis quam repellat cumque maxime provident laboriosam totam nisi qui tempora. Minima officiis ipsam magni, illum recusandae veritatis?
Voluptas possimus assumenda asperiores facilis iure magni impedit similique sequi, repellendus accusantium aut culpa consectetur quisquam veritatis, dignissimos blanditiis. Sunt ipsam ex cumque ipsum explicabo, corporis quaerat voluptatem praesentium necessitatibus.</div>`
	};
</script>

<p class=" p-2"><span class="font-bold">$trigger</span> = {JSON.stringify($trigger)}</p>
<p class=" p-2"><span class="font-bold">$content</span> ={JSON.stringify($content)}</p>
<p class=" p-2"><span class="font-bold">$open</span> ={JSON.stringify($open)}</p>
<p class=" p-2"><span class="font-bold">$arrow</span> ={JSON.stringify($arrow)}</p>
<p class=" p-2"><span class="font-bold">$close</span> ={JSON.stringify($close)}</p>

<div class="flex w-1/2 items-cemter bg-pink-200">
	<button
		type="button"
		class="inline-flex ml-48 h-12 w-12 items-center justify-center rounded-full bg-blue-600 text-white
		text-sm font-medium hover:opacity-60
		focus-visible:ring focus-visible:ring-blue-400 focus-visible:ring-offset-2 mt-4"
		{...$trigger}
		use:trigger
		aria-label="Update dimensions">
		TEST
		<span class="sr-only">Open Popover</span>
	</button>

	{#if $open}
		<div
			{...$content}
			use:content
			transition:fade={{ duration: 100 }}
			class="z-10 w-1/2 rounded-lg bg-red-500 shadow-sm border border-blue-600">
			<!-- <div {...$arrow} style="width:var(--arrow-size, 12px);height:var(--arrow-size, 12px)"/> -->
			<div class="flex flex-col">
				<div
					class="relative pt-1 h-8 text-center font-medium text-neutral-100 bg-blue-500 font-semibold rounded-t-lg">
					{@html popoverInfoHTML.head}
					<button
						class=" absolute right-1.5 top-0.5 flex h-7 w-7 items-center justify-center rounded-full
									text-blue-600 hover:bg-blue-200 focus-visible:ring focus-visible:ring-blue-400 focus-visible:ring-offset-2
									bg-white p-0 text-sm font-medium"
						{...close}
						use:close>
						X
					</button>
				</div>
				{@html popoverInfoHTML.body}
			</div>
		</div>
	{/if}
</div>
