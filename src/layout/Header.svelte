<script lang="ts">
  import { Switch } from 'malachite-ui/components';

  export let isMonthly: boolean;
</script>

<header class="bounding w-full min-w-xs mx-auto | flex flex-col items-center gap-6">
  <h1 class="text-3xl text-slate-600">Our Pricing</h1>
  <div class="flex items-center gap-6">
    <button
      class="text-slate-300 | hover:text-slate-700 focus:text-slate-700"
      on:click={() => (isMonthly = false)}
      aria-label="Set Annually Prices">
      Annually
    </button>
    <Switch
      class="relative h-9 w-18 min-h-8 min-w-16 | flex items-center | bg-gradient-r rounded-full lighten"
      bind:checked={isMonthly}>
      <span class="sr-only">
        Toggle {isMonthly ? 'Annually' : 'Monthly'} Prices
      </span>
      <span
        class="absolute h-8 w-8 | inline-block | bg-white rounded-full transform transition {isMonthly
          ? 'translate-x-9.5'
          : 'translate-x-0.5'}"
        aria-hidden="true" />
    </Switch>
    <button
      class="text-slate-300 | hover:text-slate-700 focus:text-slate-700"
      on:click={() => (isMonthly = true)}
      aria-label="Set Monthly Prices">
      Monthly
    </button>
  </div>
</header>

<style global>
  .lighten:hover,
  .lighten:focus {
    box-shadow: inset 0 0 100px 100px rgba(255, 255, 255, 0.5);
  }
</style>
