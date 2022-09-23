<script lang="ts">
  export let title: string;
  export let name: string;
  export let options: number[];
  export let selected = options[0] || 0;
</script>

<div class="custom-radio">
  <div class="title">{title}</div>
  <div class="options">
    {#each options as value}
      <label>
        <input type="radio" bind:group={selected} {name} {value} />
        <div class="box">
          <span>{value}</span>
        </div>
      </label>
    {/each}
  </div>
</div>

<style>
  .custom-radio {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .title {
    font-weight: bold;
    margin-bottom: 0.5rem;
  }

  .options {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }

  input[type='radio'] {
    display: none;
  }

  input[type='radio']:checked + .box {
    background: var(--light-gold-color);
    transform: translateY(-4px) rotateZ(6deg);
  }

  .box {
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    height: 32px;
    width: 32px;
    margin: 1px;
    will-change: transform;
    transition: transform 300ms;
    border: 1px solid var(--dark-blue-color);
    color: var(--dark-blue-color);
  }
</style>
