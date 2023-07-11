<script lang="ts">
  import { createPopover } from '@melt-ui/svelte';
  import { fade } from 'svelte/transition';

  const { trigger, content, open, arrow, close } = createPopover();
	$: console.log("$trigger", $trigger)
</script>
 
 <div class="flex w-full justify-center">
 <button
  type="button"
  class="	inline-flex h-12 w-12 items-center justify-center rounded-full bg-blue-600 text-white
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
    class="z-10 w-60 rounded-[4px] bg-white p-5 shadow-sm"
  >
    <div {...$arrow} />
    <div class="flex flex-col gap-2.5">
      <p>Dimensions</p>
      <fieldset>
        <label for="width"> Width </label>
        <input id="width" value="100%" class= "flex h-8 w-full rounded-md border border-blue-800 bg-transparent px-2.5 text-sm ring-offset-blue-300 focus-visible:ring focus-visible:ring-blue-400 focus-visible:ring-offset-1 flex-1 items-center justify-center px-2.5 text-sm leading-none text-blue-700" />
      </fieldset>
      <fieldset>
        <label for="maxWidth"> Max. width </label>
        <input id="maxWidth" value="300px" class= "flex h-8 w-full rounded-md border border-blue-800 bg-transparent px-2.5 text-sm ring-offset-blue-300 focus-visible:ring focus-visible:ring-blue-400 focus-visible:ring-offset-1 flex-1 items-center justify-center px-2.5 text-sm leading-none text-blue-700" />
      </fieldset>
      <fieldset>
        <label for="height"> Height </label>
        <input id="height" value="25px" class= "flex h-8 w-full rounded-md border border-blue-800 bg-transparent px-2.5 text-sm ring-offset-blue-300 focus-visible:ring focus-visible:ring-blue-400 focus-visible:ring-offset-1 flex-1 items-center justify-center px-2.5 text-sm leading-none text-blue-700" />
      </fieldset>
      <fieldset>
        <label for="maxHeight"> Max. height </label>
        <input id="maxHeight" class= "flex h-8 w-full rounded-md border border-blue-800 bg-transparent px-2.5 text-sm ring-offset-blue-300 focus-visible:ring focus-visible:ring-blue-400 focus-visible:ring-offset-1 flex-1 items-center justify-center px-2.5 text-sm leading-none text-blue-700" />
      </fieldset>
    </div>
    <button class="
		absolute right-1.5 top-1.5 flex h-7 w-7 items-center justify-center rounded-full
		text-blue-900 transition-colors hover:bg-blue-500/10
		focus-visible:ring focus-visible:ring-blue-400 focus-visible:ring-offset-2
		bg-white p-0 text-sm font-medium" {...close} use:close>
      X
    </button>
  </div>
{/if}
 
 </div>

