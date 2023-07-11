<script lang="ts">
  import { createPopover } from '@melt-ui/svelte';
  import { fade } from 'svelte/transition';

  const { trigger, content, open, arrow, close } = createPopover();
export let popoverInfoHTML = {
		head: `<div class="mb-2 font-medium text-neutral-900 font-semibold">ListItemTop from PopInfo</div>`,
		body: `<div class="text-left">Lorem ipsum  sit  consectetur</div>`
	};
</script>
<p class="mt-2"><span class="font-bold">$trigger</span> = {JSON.stringify($trigger)}</p>
<p class="mt-2"><span class="font-bold">$content</span> ={JSON.stringify($content)}</p>
<p class="mt-2"><span class="font-bold">$open</span> ={JSON.stringify($open)}</p>
<p class="mt-2"><span class="font-bold">$arrow</span> ={JSON.stringify($arrow)}</p>
<p class="mt-2"><span class="font-bold">$close</span> ={JSON.stringify($close)}</p>
 
 <div class="flex w-1/2 justify-end">
 
  <button
  type="button"
  class="inline-flex h-12 w-12 items-center justify-center rounded-full bg-blue-600 text-white
		text-sm font-medium hover:opacity-60
		focus-visible:ring focus-visible:ring-blue-400 focus-visible:ring-offset-2 mt-4"
  {...$trigger}
  use:trigger
  aria-label="Update dimensions"
>
TEST
  <span class="sr-only">Open Popover</span>
</button>
 

 
{#if $open}
  <div
    {...$content}
    use:content
    transition:fade={{ duration: 100 }}
    class="z-10 w-60 rounded-lg bg-neutral-200 p-2 shadow-sm border border-blue-600 "
  >
   	 <div {...$arrow}/>
    <div class="flex flex-col gap-2.5">
      {@html popoverInfoHTML.head}
			  {@html popoverInfoHTML.body}
	
	
		
      
    </div>
    <button class="
		absolute right-1.5 top-1.5 flex h-7 w-7 items-center justify-center rounded-full
		text-blue-900 hover:bg-blue-200
		focus-visible:ring focus-visible:ring-blue-400 focus-visible:ring-offset-2
		bg-white p-0 text-sm font-medium" {...close} use:close>
      X
    </button>
  </div>
{/if}
 
 </div>


 

