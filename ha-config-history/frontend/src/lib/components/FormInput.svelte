<script lang="ts">
  interface FormInputProps {
    id?: string;
    type?: string;
    placeholder?: string;
    value: string | number | undefined;
    changed?: boolean;
    min?: string;
    class?: string;
  }

  let {
    id,
    type = "text",
    placeholder = "",
    value = $bindable(),
    changed = false,
    min,
    class: className = "",
    ...restProps
  }: FormInputProps = $props();
</script>

<input
  {id}
  {type}
  {placeholder}
  {min}
  bind:value
  class="form-input {className}"
  class:changed
  {...restProps}
/>

<style>
  .form-input {
    width: 100%;
    padding: 0.6rem;
    background: var(--ha-card-background, #2c2c2e);
    border: 1px solid var(--ha-card-border-color, #3c3c3e);
    border-radius: 4px;
    color: var(--primary-text-color, #ffffff);
    font-size: 0.9rem;
  }

  .form-input:focus {
    outline: none;
    border-color: var(--primary-color, #03a9f4);
  }

  .form-input.changed {
    border-color: var(--warning-color, #ff9800);
  }

  /* Search input specific styles */
  .form-input.search-input {
    width: 80%;
    background: var(--ha-card-background, #1c1c1e);
    border: 1px solid var(--ha-card-border-color, #2c2c2e);
    color: var(--primary-text-color, #ffffff);
    font-size: 0.9rem;
  }

  .form-input.search-input:focus {
    outline: none;
    border-color: var(--primary-color, #03a9f4);
  }
</style>
