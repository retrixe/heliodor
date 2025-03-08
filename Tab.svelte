<!-- Copyright 2025 Ibrahim Ansari -->
<!-- SPDX-License-Identifier: Apache-2.0 -->

<script lang="ts">
  import { page } from '$app/state'
  import type { Snippet } from 'svelte'

  const {
    children,
    href,
    onclick,
    active,
  }: { children: Snippet; href?: string; onclick?: () => void; active?: boolean } = $props()

  const highlighted = !!active || page.url.pathname === href
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
