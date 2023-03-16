<script>
  // @ts-nocheck

  export let helpboxOpen = false;
  export let commands = [
    {
      command: "Products",
      description: "Will take you to the recommended products",
    },
    {
      command: "Products",
      description: "Will take you to the recommended products",
    },
  ];
</script>

{#if helpboxOpen}
  <div class="fixed bottom-5 right-5  max-w-xs  flex flex-col gap-3 ">
    <div class="flex justify-between">
      <div>You can say:</div>
      <button
        class="hover:scale-90 transition-all"
        on:click={() => (helpboxOpen = false)}
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 24 24"
          stroke-width="1.5"
          stroke="currentColor"
          class="w-6 h-6"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M6 18L18 6M6 6l12 12"
          />
        </svg>
      </button>
    </div>
    {#each commands as command}
      <div class="flex flex-col rounded-xl bg-gray-100 border p-4 border-black">
        <div class=" font-bold">{command.command}</div>
        <div class="text-sm">{command.description}</div>
      </div>
    {/each}
  </div>
{:else}
  <button
    on:click={() => (helpboxOpen = true)}
    class=" bottom-5 fixed right-5 py-3 text-white font-bold px-8 bg-black rounded-full hover:scale-90 transition-all"
  >
    Available Commands
  </button>
{/if}
