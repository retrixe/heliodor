<!-- Copyright 2025 Ibrahim Ansari -->
<!-- SPDX-License-Identifier: Apache-2.0 -->

<!-- NOTE: This component is experimental! -->

<script lang="ts">
  import type { Snippet } from 'svelte'

  const { children, header, footer }: { children: Snippet; header?: Snippet; footer?: Snippet } =
    $props()
</script>

<nav class="navigation-rail">
  {@render header?.()}
  <div class="items">
    {@render children()}
  </div>
  {@render footer?.()}
</nav>

<style lang="scss">
  .navigation-rail {
    padding: 1rem;
    width: 7rem;
    min-height: 0;
    background-color: var(--primary-color);
    display: flex;
    flex-direction: column;
    align-items: center;

    :global(button) {
      width: 100%;
      flex-direction: column;
      font-weight: normal;
      padding: 0.5rem;
      gap: 4px;
    }
  }

  .items {
    flex-grow: 1;
    gap: 8px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
</style>
