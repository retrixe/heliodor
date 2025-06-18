<!-- Copyright 2025 Ibrahim Ansari -->
<!-- SPDX-License-Identifier: Apache-2.0 -->

<!-- Derived from Button.svelte -->

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

    border: none;
    border-radius: 0.5rem;
    cursor: pointer;
    font-weight: bold;

    /* Compared to Button:
      - Different background / background-color -> color / hover brightness / padding.
      - Added background color with transition.
    */
    padding: 0.25rem;
    background: none;
    &.primary {
      color: var(--primary-color);
    }
    &.success {
      color: green;
    }
    &.error {
      color: var(--error-color);
    }
    transition:
      filter 0.2s ease-in-out,
      background-color 0.2s ease-in-out;
    &:enabled {
      &:hover {
        filter: brightness(0.8);
        background-color: var(--surface-color);
      }
      &:active {
        filter: brightness(0.6);
      }
    }
    &:disabled {
      color: var(--divider-color);
      cursor: not-allowed;
    }
  }
</style>
