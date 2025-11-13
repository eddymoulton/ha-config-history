<script lang="ts">
  interface FormSelectProps {
    id?: string;
    value: string;
    class?: string;
    children?: any;
  }

  let {
    id,
    value = $bindable(),
    class: className = "",
    children,
    ...restProps
  }: FormSelectProps = $props();
</script>

<select
  {id}
  bind:value
  class="form-select {className}"
  {...restProps}
>
  {@render children?.()}
</select>

<style>
  .form-select {
    width: 100%;
    padding: 0.6rem;
    background: var(--ha-card-background, #2c2c2e);
    border: 1px solid var(--ha-card-border-color, #3c3c3e);
    border-radius: 4px;
    color: var(--primary-text-color, #ffffff);
    font-size: 0.9rem;
  }

  .form-select:focus {
    outline: none;
    border-color: var(--primary-color, #03a9f4);
  }

  /* Group select specific styles */
  .form-select.group-select {
    flex: 1;
    padding: 0.5rem;
    background: var(--ha-card-background, #1c1c1e);
    border: 1px solid var(--ha-card-border-color, #2c2c2e);
    border-radius: 4px;
    color: var(--primary-text-color, #ffffff);
    font-size: 0.9rem;
  }

  .form-select.group-select:focus {
    outline: none;
    border-color: var(--primary-color, #03a9f4);
  }
</style>