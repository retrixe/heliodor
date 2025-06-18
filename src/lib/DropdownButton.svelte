<!-- Copyright 2025 Ibrahim Ansari -->
<!-- SPDX-License-Identifier: Apache-2.0 -->

<script lang="ts">
  import type { Snippet } from 'svelte'
  import Button, { type Props } from './Button.svelte'

  const {
    primaryChild,
    secondaryChild,
    children,
    primary = {},
    secondary = {},
  }: {
    primaryChild: Snippet
    secondaryChild: Snippet
    children?: Snippet
    primary?: Omit<Props, 'children'>
    secondary?: Omit<Props, 'children'>
  } = $props()
</script>

<div class="dropdown-button">
  <Button {...primary}>{@render primaryChild()}</Button>
  <Button {...secondary}>{@render secondaryChild()}</Button>
  {@render children?.()}
</div>

<style lang="scss">
  .dropdown-button {
    position: relative;
    display: flex;
    gap: 0.125rem;
    > :global(button:first-child) {
      border-radius: 0.5rem 0 0 0.5rem;
    }
    > :global(button:nth-child(2)) {
      border-radius: 0 0.5rem 0.5rem 0;
      padding: 0.5rem;
    }
  }
</style>
