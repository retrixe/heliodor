<!-- Copyright 2025 Ibrahim Ansari -->
<!-- SPDX-License-Identifier: Apache-2.0 -->

<!-- NOTE: This component is experimental! It will likely be merged into LinearProgress. -->

<script lang="ts">
  import type { SvelteHTMLElements } from 'svelte/elements'

  type Props = SvelteHTMLElements['div'] & { percentage?: number; color?: string }
  const { percentage, color, ...rest }: Props = $props()

  const width = $derived(`${percentage ?? 0}%`)
</script>

<div class:progress-bar={true} {...rest}>
  <div class="progress-bar-filling" style:width style:background-color={color}></div>
</div>

<style lang="scss">
  .progress-bar {
    flex: 1;
    height: 8px;
    background-color: grey;
    border-radius: 4px;
    display: flex;
  }

  .progress-bar-filling {
    border-radius: inherit;
  }
</style>
