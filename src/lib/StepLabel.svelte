<script lang="ts">
  export let num: number;
</script>

<div class="num">{num}</div>

<style>
  .num {
    border-right: 0;
    background: var(--white-color);
    border-radius: 50% 0 0 50%;
    font-weight: bold;
    font-size: 1.5rem;
    height: 1rem;
    width: 1rem;
    line-height: 1rem;
    text-align: center;
    padding: 1rem;
    margin-bottom: 0.5rem;
    margin-right: -4px;
    color: var(--light-blue-color);
    border: 4px solid var(--dark-blue-color);
    box-shadow: 4px 4px 0 0 var(--dark-blue-color);
  }

  @media screen and (max-width: 768px) {
    .num {
      height: 0.5rem;
      width: 0.5rem;
      line-height: 0.5rem;
      font-size: 1rem;
    }
  }
</style>
