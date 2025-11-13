<script lang="ts">
	import type { HTMLButtonAttributes } from 'svelte/elements';
	import Button from './Button.svelte';

	interface $$Props extends HTMLButtonAttributes {
		icon: string;
		variant?: 'primary' | 'secondary' | 'success' | 'danger' | 'outlined' | 'ghost';
		size?: 'small' | 'medium' | 'large';
		loading?: boolean;
		class?: string;
		label?: string;
	}

	export let icon: $$Props['icon'];
	export let variant: $$Props['variant'] = 'ghost';
	export let size: $$Props['size'] = 'medium';
	export let loading: $$Props['loading'] = false;
	export let label: $$Props['label'] = undefined;
	let className: $$Props['class'] = '';
	export { className as class };

	$: iconButtonClass = [
		'icon-btn',
		`icon-btn-${size}`,
		className
	]
		.filter(Boolean)
		.join(' ');
</script>

<Button
	class={iconButtonClass}
	{variant}
	{loading}
	on:click
	on:mouseenter
	on:mouseleave
	on:focus
	on:blur
	aria-label={label || $$restProps['aria-label']}
	{...$$restProps}
>
	{#if !loading}
		<span class="icon-btn-content" aria-hidden="true">{icon}</span>
	{/if}
</Button>

<style>
	:global(.icon-btn) {
		padding: 0.25rem !important;
		aspect-ratio: 1;
		min-width: unset;
	}

	:global(.icon-btn-small) {
		width: 1.75rem;
		height: 1.75rem;
		font-size: 1rem;
	}

	:global(.icon-btn-medium) {
		width: 2rem;
		height: 2rem;
		font-size: 1.1rem;
	}

	:global(.icon-btn-large) {
		width: 2.5rem;
		height: 2.5rem;
		font-size: 1.3rem;
	}

	:global(.icon-btn.btn-ghost:hover:not(:disabled)) {
		transform: scale(1.1);
	}

	:global(.icon-btn.btn-ghost.btn-danger:hover:not(:disabled)) {
		opacity: 1;
		background: rgba(244, 67, 54, 0.1);
	}

	:global(.icon-btn.btn-ghost.btn-danger) {
		opacity: 0.7;
	}

	.icon-btn-content {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 100%;
		height: 100%;
	}
</style>