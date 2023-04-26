<script lang="ts">
	import { getContext, setContext } from 'svelte';
	import type { Writable } from 'svelte/store';
	import Counter from './Counter.svelte';

	export let className: string;

	let clickCount = getContext<Writable<number>>('clickCount');
	let items = getContext<Writable<Record<string, number>>>('items');

	const handleClick = () => {
		clickCount.update((current) => current + 1);
	};

	let showCount: boolean;

	$: {
		showCount = $clickCount > 0 || Object.values($items).find((item) => item > 0) !== undefined;
	}
</script>

<button
	class={`inline-flex items-center rounded-full bg-white shadow transition-transform hover:scale-105 active:scale-100 ${className}`}
	on:click={handleClick}
>
	<slot />
	<div
		class={`text-xl overflow-hidden transition-all ${
			showCount ? 'px-16 max-w-48' : 'px-0 max-w-0'
		} `}
	>
		<Counter count={$clickCount} />
	</div>
</button>
