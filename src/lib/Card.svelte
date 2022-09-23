<script lang="ts">
  export let title;
</script>

<div class="card">
  <h1 class="title">
    {title}
  </h1>
  <slot />
</div>

<style>
  .card {
    display: flex;
    align-items: center;
    flex-direction: column;
    padding: 1.5rem;
    width: 50%;
    border-radius: var(--border-radius);
    border: 4px solid var(--dark-blue-color);
    box-shadow: 8px 8px 0 0 var(--dark-blue-color);
    background: rgb(224, 237, 245);
    background: linear-gradient(90deg, rgba(224, 237, 245, 1) 0%, rgba(255, 255, 255, 1) 100%);
  }

  .title {
    font-weight: bold;
    font-size: 2em;
    margin: 0 0 1rem 0;
    color: var(--red-color);
  }

  @media screen and (max-width: 768px) {
    .card {
      width: 100%;
    }

    .title {
      font-size: 1.2em;
    }
  }
</style>
