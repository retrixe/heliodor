<!-- Copyright 2025 Ibrahim Ansari -->
<!-- SPDX-License-Identifier: Apache-2.0 -->

<script lang="ts">
  import type { HTMLAnchorAttributes } from 'svelte/elements'

  const { highlighted, ...props }: HTMLAnchorAttributes & { highlighted?: boolean } = $props()
</script>

<a {...props} class:uncolored={!highlighted}>
  {@render props.children?.()}
</a>

<style lang="scss">
  a {
    text-decoration: none;
    font-weight: bold;
  }

  .uncolored {
    color: inherit;
  }
</style>
