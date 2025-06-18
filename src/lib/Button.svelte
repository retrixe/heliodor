<!-- Copyright 2025 Ibrahim Ansari -->
<!-- SPDX-License-Identifier: Apache-2.0 -->

<script lang="ts">
  import type { Snippet } from 'svelte'
  import type { HTMLButtonAttributes } from 'svelte/elements'

  export type Props = HTMLButtonAttributes & {
    children: Snippet
    color?: 'default' | 'primary' | 'success' | 'error'
  }
  const { color, children, ...rest }: Props = $props()
</script>

<button class={color} {...rest}>{@render children()}</button>

<style lang="scss">
  button {
    display: inline-flex;
    justify-content: center;
    align-items: center;

    padding: 0.5rem 1.5rem;
    color: white;
    background-color: var(--primary-color);
    &.success {
      background-color: green;
    }
    &.error {
      background-color: var(--error-color);
    }
    border: none;
    border-radius: 0.5rem;
    cursor: pointer;
    font-weight: bold;
    transition: filter 0.2s ease-in-out;
    &:enabled {
      &:hover {
        filter: brightness(1.2);
      }
      &:active {
        filter: brightness(0.8);
      }
    }
    &:disabled {
      background-color: var(--divider-color);
      cursor: not-allowed;
    }
  }
</style>
