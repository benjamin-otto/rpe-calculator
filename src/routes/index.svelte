<script context="module" lang="ts">
  export const prerender = true;
</script>

<script lang="ts">
  import StepLabel from '$lib/StepLabel.svelte';
  import E1RMCalc from '$lib/E1RMCalc.svelte';
  import RpeWeightCalc from '$lib/RPEWeightCalc.svelte';
</script>

<svelte:head>
  <title>e1RM & RPE Calculator</title>
</svelte:head>

<div class="content">
  <div class="step">
    <StepLabel num={1} />
    <E1RMCalc />
  </div>
  <div class="step">
    <StepLabel num={2} />
    <RpeWeightCalc />
  </div>
</div>

<style>
  .content {
    margin: 0 auto;
  }

  .step {
    display: flex;
    justify-content: center;
    margin-bottom: 1rem;
  }
</style>
