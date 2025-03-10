<!-- Copyright 2025 Ibrahim Ansari -->
<!-- SPDX-License-Identifier: Apache-2.0 -->

<script lang="ts">
  import type { Snippet } from 'svelte'

  const { children }: { children: Snippet } = $props()
</script>

<div class="top-bar">
  {@render children()}
</div>

<div class="top-bar-spacer"></div>

<style lang="scss">
  .top-bar {
    z-index: 100;
    height: 4rem;
    position: fixed;
    display: flex;
    width: 100%;
    justify-content: space-between;
    align-items: center;
    padding: 1rem;
    backdrop-filter: blur(12px);
    border-bottom: 1px solid var(--divider-color);
  }

  .top-bar-spacer {
    margin-top: 4rem;
  }
</style>
