<script lang="ts">
  import type { Snippet } from 'svelte'

  const { children }: { children: Snippet } = $props()
</script>

<div class="tabs">
  {@render children()}
</div>

<style lang="scss">
  .tabs {
    display: flex;
    width: 100%;
    border-radius: 8px;
    border: 1px solid var(--divider-color);
    > :global(.tab) + :global(.tab) {
      border-left: 1px solid var(--divider-color);
    }
  }
</style>
