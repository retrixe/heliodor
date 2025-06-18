<!-- Copyright 2025 Ibrahim Ansari -->
<!-- SPDX-License-Identifier: Apache-2.0 -->

<script lang="ts">
  import type { Snippet } from 'svelte'
  import { slide } from 'svelte/transition'

  interface Props {
    message?: string
    duration?: number
    onclose: () => void
    icon?: Snippet
    footer?: Snippet
    color?: 'success' | 'error' | 'primary'
  }

  const { message, duration, icon, footer, color, onclose: handleClose }: Props = $props()

  const appliedColor = $derived(
    color === 'error'
      ? 'var(--error-color)'
      : color === 'success'
        ? 'green'
        : color === 'primary'
          ? 'var(--primary-color)'
          : undefined,
  )

  $effect(() => {
    if (duration && duration > 0) {
      const timeout = setTimeout(handleClose, duration)
      return () => clearTimeout(timeout)
    }
  })
</script>

<div
  class="toast"
  transition:slide={{ duration: 300, axis: 'y' }}
  role="alert"
  aria-live="assertive"
  style:border-bottom={appliedColor ? '2px solid ' + appliedColor : undefined}
>
  {#if icon}
    <div class="buttons" style:color={appliedColor}>{@render icon()}</div>
  {/if}
  <span class="message">{message}</span>
  {#if footer}
    <div class="buttons" style:color={appliedColor}>{@render footer()}</div>
  {/if}
</div>

<style lang="scss">
  .toast {
    position: fixed;
    bottom: 2rem;
    left: 50%;
    transform: translateX(-50%);
    pointer-events: auto; // Allow interaction even scrolllock is applied (Dialog)
    z-index: 200;

    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 1rem;

    padding: 1rem;
    border-radius: 0.5rem;
    background-color: var(--surface-color);
    box-shadow: 0 0 1rem rgba(0, 0, 0, 0.2);

    width: 90vw;
    @media (min-width: 600px) {
      min-width: 480px;
      width: unset;
    }
  }

  .buttons {
    display: flex;
    flex-shrink: 0;
  }

  .message {
    flex-grow: 1;
  }
</style>
