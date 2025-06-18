<!-- Copyright 2025 Ibrahim Ansari -->
<!-- SPDX-License-Identifier: Apache-2.0 -->

<!-- Note: This component has shortcomings being worked out. The API will change drastically. -->

<script lang="ts">
  import { Button } from 'heliodor'
  import type { Snippet } from 'svelte'
  import { slide } from 'svelte/transition'

  interface Props {
    message?: string
    duration?: number
    onclose: () => void
    icon?: Snippet<[string | undefined]>
    color?: 'success' | 'error' | 'primary'
  }

  const { message, duration, icon, color, onclose: handleClose }: Props = $props()

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
    {@render icon(appliedColor)}
  {/if}
  <span class="message">{message}</span>
  <!-- TODO: We need an icon variant of Button, and we don't want this down here -->
  <Button class="close-button" onclick={handleClose} aria-label="Close">
    <!-- https://phosphoricons.com/?q=x -->
    <svg
      xmlns="http://www.w3.org/2000/svg"
      width="1.5rem"
      height="1.5rem"
      fill="var(--color)"
      viewBox="0 0 256 256"
    >
      <path
        d="M205.66,194.34a8,8,0,0,1-11.32,11.32L128,139.31,61.66,205.66a8,8,0,0,1-11.32-11.32L116.69,128,50.34,61.66A8,8,0,0,1,61.66,50.34L128,116.69l66.34-66.35a8,8,0,0,1,11.32,11.32L139.31,128Z"
      ></path>
    </svg>
  </Button>
</div>

<style lang="scss">
  .toast {
    position: fixed;
    bottom: 2rem;
    left: 50%;
    transform: translateX(-50%);
    /* TODO: Misbehaviour when used with Dialog. */
    z-index: 200;

    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 1rem;

    /* TODO: Deal with the widths */
    min-width: 320px;
    max-width: 90%;
    padding: 1rem;
    border-radius: 0.5rem;
    background-color: var(--surface-color);
    box-shadow: 0 0 1rem rgba(0, 0, 0, 0.2);
  }

  .message {
    flex-grow: 1;
  }

  .toast > :global(button.close-button) {
    background: none;
    padding: 0 0.25rem;
    opacity: 0.7;
    transition: opacity 0.2s;

    &:hover {
      opacity: 1;
    }
  }
</style>
