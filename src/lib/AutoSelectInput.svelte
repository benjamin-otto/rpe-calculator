<script lang="ts">
  export let label: string;
  export let value: number;

  function handleFocus(e) {
    e.target.select();
  }
</script>

<label for={label}>{label}</label>
<input type="number" name={label} id={label} min="0" bind:value on:focus={handleFocus} />

<style>
  label {
    margin-bottom: 0.5rem;
  }

  input {
    width: 100%;
  }
</style>
