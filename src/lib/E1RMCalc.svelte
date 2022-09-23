<script lang="ts">
  import { e1rm } from './stores';
  import Card from './Card.svelte';
  import CustomRadio from './CustomRadio.svelte';
  import AutoSelectInput from './AutoSelectInput.svelte';

  let reps: number;
  let weight = 0;
  $: e1rm.set(Math.round(weight / (1.0278 - 0.0278 * reps)));
</script>

<Card title="Calculate e1RM">
  <div class="content">
    <div class="inputs">
      <CustomRadio
        title="Reps"
        name="e1rm-reps"
        options={[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]}
        bind:selected={reps}
      />
      <AutoSelectInput label="Weight" bind:value={weight} />
    </div>
    <div class="output">
      <div class="weight">{$e1rm}</div>
      <div>e1RM</div>
    </div>
  </div>
</Card>

<style>
  .content {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
  }

  .inputs {
    flex: 1;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  :global(.inputs > div:first-of-type) {
    margin-bottom: 2rem;
  }

  /* .output {
    flex: 1;
    font-size: 4rem;
    text-align: center;
    color: var(--light-blue-color);
  } */

  .output {
    flex: 1;
    text-align: center;
  }

  .weight {
    font-size: 4rem;
    color: var(--light-blue-color);
  }

  @media screen and (max-width: 768px) {
    .content {
      flex-direction: column;
    }

    .output {
      font-size: 3rem;
      margin-top: 2rem;
    }
  }
</style>
