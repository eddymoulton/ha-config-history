<script lang="ts">
  import Alert from './components/Alert.svelte';

  type Props = {
    loading?: boolean;
    error?: string | null;
    empty?: boolean;
    emptyMessage?: string;
    loadingMessage?: string;
  };

  let {
    loading = false,
    error = null,
    empty = false,
    emptyMessage = "No items found",
    loadingMessage = "Loading...",
  }: Props = $props();
</script>

{#if loading}
  <div class="loading" role="status" aria-live="polite">{loadingMessage}</div>
{:else if error}
  <Alert type="error" message="Error: {error}" />
{:else if empty}
  <div class="empty">{emptyMessage}</div>
{/if}

<style>
  .loading,
  .empty {
    text-align: center;
    padding: 3rem 1.5rem;
    color: var(--secondary-text-color, #9b9b9b);
    font-size: 1rem;
  }
</style>
