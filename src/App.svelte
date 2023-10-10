<script lang="ts">
  let counter = 0;
</script>

<main>
  <div class="counter">
    <button on:click={() => {counter += 1}}>+</button>
      <b>{counter}</b>
    <button on:click={() => {counter -= 1}}>-</button>
  </div>
</main>

<style>
  .counter{
    background: bisque;
    padding: 1rem;
    border-radius: 0.8rem;
  }
</style>
