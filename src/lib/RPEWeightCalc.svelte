<!-- Store Auto-Subscriptions do not work with lang="ts"
https://github.com/sveltejs/svelte-preprocess/issues/98 -->
<script>
  import { e1rm } from './stores';
  import Card from './Card.svelte';
  import CustomRadio from './CustomRadio.svelte';

  let reps = 1;
  let rpe = 6;

  let rpeMapping = new Map([
    [6, [0.863, 0.837, 0.811, 0.786, 0.762, 0.739, 0.707, 0.68, 0.653, 0.626, 0.599, 0.572]],
    [6.5, [0.878, 0.85, 0.824, 0.799, 0.774, 0.751, 0.723, 0.694, 0.667, 0.64, 0.613, 0.586]],
    [7, [0.892, 0.863, 0.837, 0.811, 0.786, 0.762, 0.739, 0.707, 0.68, 0.653, 0.626, 0.599]],
    [7.5, [0.907, 0.878, 0.85, 0.824, 0.799, 0.774, 0.751, 0.723, 0.694, 0.667, 0.64, 0.613]],
    [8, [0.922, 0.892, 0.863, 0.837, 0.811, 0.786, 0.762, 0.739, 0.707, 0.68, 0.653, 0.626]],
    [8.5, [0.939, 0.907, 0.878, 0.85, 0.824, 0.799, 0.774, 0.751, 0.723, 0.694, 0.667, 0.64]],
    [9, [0.955, 0.922, 0.892, 0.863, 0.837, 0.811, 0.786, 0.762, 0.739, 0.707, 0.68, 0.653]],
    [9.5, [0.98, 0.94, 0.91, 0.88, 0.85, 0.82, 0.8, 0.774, 0.751, 0.723, 0.694, 0.67, 0.64, 0.613]],
    [10, [1, 0.955, 0.922, 0.892, 0.863, 0.837, 0.811, 0.786, 0.762, 0.739, 0.707, 0.68]]
  ]);

  $: rpeWeight = Math.round($e1rm * rpeMapping.get(rpe)[reps - 1]);
  $: percentage = Math.round(rpeMapping.get(rpe)[reps - 1] * 100);
</script>

<Card title="Calculate RPE Weight">
  <div class="content">
    <div class="inputs">
      <CustomRadio
        title="Reps"
        name="rpe-reps"
        options={[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]}
        bind:selected={reps}
      />
      <CustomRadio
        title="RPE"
        name="rpe-rpe"
        options={[6, 6.5, 7, 7.5, 8, 8.5, 9, 9.5, 10]}
        bind:selected={rpe}
      />
    </div>
    <div class="output">
      <div class="weight">{rpeWeight}</div>
      <div>{percentage}% of {$e1rm}</div>
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
      margin-top: 2rem;
    }

    .weight {
      font-size: 3rem;
    }
  }
</style>
