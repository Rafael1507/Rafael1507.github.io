<script>
    import Produto from '$lib/components/Produto.svelte';
    import { cards } from '$lib/data.js';
  </script>

<br>
<center>
  <div class="row g-4">
    {#each cards as card}
      <div class="col">
        <Produto {...card} />
      </div>
    {/each}
  </div>
</center>