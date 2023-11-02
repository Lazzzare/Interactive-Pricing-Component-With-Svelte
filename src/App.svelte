<script lang="ts">
  import Header from "./lib/Header.svelte";
  import PricingCard from "./lib/PricingCard.svelte";

  let monthly = true;
  let rangeValue = 0;
  let initialRange = 8;
  let initialpageViews = 10;
</script>

<main class="w-full h-screen">
  <Header />
  <PricingCard {rangeValue} {initialRange} {initialpageViews} {monthly} />
</main>
