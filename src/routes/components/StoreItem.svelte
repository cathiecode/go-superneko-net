<script lang="ts">
	import { getContext } from 'svelte';
	import ListItem from './ListItem.svelte';
	import type { Writable } from 'svelte/store';

	export let price: number;
	export let name: string;
	export let id: string;
	export let rate: number;

	let clickCount = getContext<Writable<number>>('clickCount');
	let items = getContext<Writable<Record<string, number>>>('items');

	let show: Boolean;

	const handleClick = () => {
		// FIXME: Atomic change
		if ($clickCount - price >= 0) {
			clickCount.update((count) => count - price);
			items.update((items) => ({ ...items, [id]: items[id] + 1 }));
		}
	};

	$: {
		show = $clickCount >= price || $items[id] > 0;
	}
</script>

{#if show}
	<ListItem on:click={handleClick}>
		<span slot="icon">
			<slot name="icon" />
		</span>
		<span slot="title"
			>{name}
			({$items[id]} * {rate}<img
				class="inline w-auto h-[1em]"
				src="/images/superneko.svg"
				alt="Illustration of a rainbow-colored cat"
			/>/s cost: {price}<img
				class="inline w-auto h-[1em]"
				src="/images/superneko.svg"
				alt="Illustration of a rainbow-colored cat"
			/>)</span
		>
	</ListItem>
{/if}
