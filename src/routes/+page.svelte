<script lang="ts">
	import { createPopover } from '@melt-ui/svelte';
	import { fade } from 'svelte/transition';

	const { trigger, content, open, arrow, close } = createPopover();
	// $arrow.style = "position:absolute;width:var(--arrow-size, 12px);height:var(--arrow-size, 12px);"

	export let popoverInfoHTML = {
		head: `ListItemTop from PopInfo`,
		body: 
		`<div>Lorem ipsum dolor sit amet consectetur adipisicing elit. Porro illum at similique iure aut, quis blanditiis, exercitationem maiores accusamus cupiditate recusandae quo magni sunt ipsum sequi? Eaque illum excepturi suscipit!
Cupiditate esse quo nesciunt dolores repudiandae soluta a impedit odio, ducimus ab nobis quam repellat cumque maxime provident laboriosam totam nisi qui tempora. Minima officiis ipsam magni, illum recusandae veritatis?
Voluptas possimus assumenda asperiores facilis iure magni impedit similique sequi, repellendus accusantium aut culpa consectetur quisquam veritatis, dignissimos blanditiis. Sunt ipsam ex cumque ipsum explicabo, corporis quaerat voluptatem praesentium necessitatibus.</div>`
	};
</script>

<p class=" p-2"><span class="font-bold">$trigger</span> = {JSON.stringify($trigger)}</p>
<p class=" p-2"><span class="font-bold">$content</span> ={JSON.stringify($content)}</p>
<p class=" p-2"><span class="font-bold">$open</span> ={JSON.stringify($open)}</p>
<p class=" p-2"><span class="font-bold">$arrow</span> ={JSON.stringify($arrow)}</p>
<p class=" p-2"><span class="font-bold">$close</span> ={JSON.stringify($close)}</p>

<div>
	<button type="button" {...$trigger} use:trigger aria-label="Update dimensions">
		TEST
		<span class="sr-only">Open Popover</span>
	</button>

	{#if $open}
		<div {...$content} use:content transition:fade={{ duration: 100 }}>
			<!-- <div {...$arrow} style="width:var(--arrow-size, 12px);height:var(--arrow-size, 12px)"/> -->
			<div>
				<div>
					{@html popoverInfoHTML.head}
					<button {...close} use:close> X </button>
				</div>
				{@html popoverInfoHTML.body}
			</div>
		</div>
	{/if}
</div>
