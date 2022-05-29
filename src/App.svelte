<script>
  import { Header } from '@layout';
  import { Card } from '@components';

  let isMonthly = true;
</script>

<Header bind:isMonthly />

<main class="bounding w-full mx-auto">
  <section class="w-full | grid gap-9 | lg:(grid-cols-3 gap-0) items-center">
    <h2 class="sr-only">Subscriptions</h2>
    <Card
      title="Basic"
      price={isMonthly ? 19.99 : 199.99}
      specs={['500 GB Storage', '2 Users Allowed', 'Send up to 3GB']} />
    <Card
      class="lg:(z-20 py-12 shadow-2xl scale-105)"
      title="Proffesional"
      price={isMonthly ? 24.99 : 249.99}
      specs={['1 TB Storage', '5 Users Allowed', 'Send up to 10GB']}
      isDark />
    <Card
      title="Proffesional"
      price={isMonthly ? 39.99 : 399.99}
      specs={['2 TB Storage', '10 Users Allowed', 'Send up to 20GB']} />
  </section>
</main>
