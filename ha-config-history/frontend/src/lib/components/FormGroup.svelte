<script lang="ts">
  interface FormGroupProps {
    label?: string;
    for?: string;
    helpText?: string;
    class?: string;
    children?: any;
  }

  let {
    label,
    for: forId,
    helpText,
    class: className = "",
    children
  }: FormGroupProps = $props();
</script>

<div class="form-group {className}">
  {#if label}
    <label for={forId}>
      {label}
      {#if helpText}
        <span class="help-text">{helpText}</span>
      {/if}
    </label>
  {/if}
  {@render children?.()}
</div>

<style>
  .form-group {
    margin-bottom: 1rem;
  }

  .form-group label {
    display: block;
    margin-bottom: 0.5rem;
    color: var(--primary-text-color, #ffffff);
    font-size: 0.9rem;
    font-weight: 500;
  }

  .help-text {
    color: var(--secondary-text-color, #9b9b9b);
    font-size: 0.8rem;
    font-weight: 400;
  }
</style>