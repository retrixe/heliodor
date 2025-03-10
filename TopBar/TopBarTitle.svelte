<!-- Copyright 2025 Ibrahim Ansari -->
<!-- SPDX-License-Identifier: Apache-2.0 -->

<script lang="ts">
  import type { Snippet } from 'svelte'

  const { children }: { children: Snippet } = $props()
</script>

<h1 class="top-bar-title">
  {@render children()}
</h1>

<style lang="scss">
  .top-bar-title {
    font-size: 1.5rem;
    line-height: 1;
    flex: 1;
  }
</style>
