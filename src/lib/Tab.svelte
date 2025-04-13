<!-- Copyright 2025 Ibrahim Ansari -->
<!-- SPDX-License-Identifier: Apache-2.0 -->

<script lang="ts">
  import type { Snippet } from 'svelte'

  interface Props {
    children: Snippet
    href?: string
    currentHref?: string | null
    onclick?: () => void
    active?: boolean
  }

  const { children, href, currentHref, onclick, active }: Props = $props()

  const highlighted = $derived(!!active || (href && currentHref && currentHref === href))
</script>

<a {href} {onclick} class="tab" class:highlighted>
  {@render children()}
</a>

<style lang="scss">
  .tab {
    display: block;
    padding: 0.2rem 1rem;
    margin: 0.6rem 0rem;
    text-align: center;
    color: var(--color);
    text-decoration: none;
  }

  .highlighted {
    font-weight: bold;
    color: var(--link-color);
  }
</style>
