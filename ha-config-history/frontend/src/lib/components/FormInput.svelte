<script lang="ts">
  interface FormInputProps {
    id?: string;
    type?: string;
    placeholder?: string;
    value: string | number | undefined;
    changed?: boolean;
    min?: string;
    style?: "search-input" | null;
    oninput?: (
      e: Event & { currentTarget: EventTarget & HTMLInputElement }
    ) => void;
  }

  let {
    id,
    type = "text",
    placeholder = "",
    value = $bindable(),
    changed = false,
    min,
    style = null,
    ...restProps
  }: FormInputProps = $props();
</script>

<input
  {id}
  {type}
  {placeholder}
  {min}
  bind:value
  class="form-input"
  class:changed
  class:search-input={style === "search-input"}
  {...restProps}
/>

<style>
  .form-input {
    width: 100%;
    padding: 0.6rem;
    background: var(--ha-card-background);
    border: 1px solid var(--ha-card-border-color);
    border-radius: 4px;
    color: var(--primary-text-color);
    font-size: 0.9rem;
  }

  .form-input:focus {
    outline: none;
    border-color: var(--primary-color);
  }

  .form-input.changed {
    border-color: var(--warning-color);
  }

  /* Search input specific styles */
  .form-input.search-input {
    width: 80%;
    background: var(--ha-card-background);
    border: 1px solid var(--ha-card-border-color);
    color: var(--primary-text-color);
    font-size: 0.9rem;
  }

  .form-input.search-input:focus {
    outline: none;
    border-color: var(--primary-color);
  }
</style>
