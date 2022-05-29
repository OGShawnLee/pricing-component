<script lang="ts" context="module">
  function toFixed(num: number, fixed: number) {
    var re = new RegExp('^-?\\d+(?:.\\d{0,' + (fixed || -1) + '})?');
    return num.toString().match(re)[0];
  }
</script>

<script lang="ts">
  import { tweened } from 'svelte/motion';
  import { quadOut } from 'svelte/easing';

  let className = '';

  export { className as class };
  export let title: string;
  export let price: number;
  export let specs: string[];
  export let href = '#';
  export let isDark = false;

  const finalPrice = tweened(price, { easing: quadOut });
  $: finalPrice.set(price);
</script>

<article
  class="min-w-300px p-8 | space-y-9 | {isDark
    ? 'bg-gradient-tb text-white'
    : 'bg-white'} shadow-lg rounded-lg transform {className} | xl:min-w-xs">
  <header class="flex flex-col items-center gap-5">
    <h3 class="text-xl {isDark ? 'text-white' : 'text-slate-600'}">{title}</h3>
    <span class="flex items-center">
      <span class="text-3xl">$</span>
      <strong class="text-6xl">{toFixed($finalPrice, 2)}</strong>
    </span>
  </header>
  <div class="flex flex-col gap-9">
    <ul class="flex flex-col items-center border-t border-slate-300/50">
      {#each specs as spec}
        <li class="w-full py-3 | border-b border-slate-300/60 text-center">{spec}</li>
      {/each}
    </ul>
    <a class="block button {isDark ? 'button--light' : 'button--dark'}" {href}> Learn More </a>
  </div>
</article>

<style>
  .button {
    @apply w-full py-3 border-2 rounded-lg uppercase text-center;
  }

  .button--dark {
    @apply bg-gradient-to-r from-gradient-light to-gradient-blue border-white text-white hover:(from-white to-white text-gradient-blue) focus:(from-white to-white border-gradient-blue text-gradient-blue);
  }

  .button--light {
    @apply bg-white border-transparent text-gradient-blue hover:(bg-transparent text-white) focus:(bg-transparent border-white text-white);
  }

  .bg-gradient-tb {
    @apply bg-gradient-to-br from-gradient-light to-gradient-blue;
  }
</style>
