<script lang="ts">
	import { writable } from 'svelte/store';
	import { onMount, setContext } from 'svelte';

	import '../index.css';

	const clickCount = writable<number>();

	clickCount.set(0);

	const items = writable<{
		kariKari: number;
		sabaCan: number;
		maguroCan: number;
		chuuru: number;
	}>();

	items.set({
		kariKari: 0,
		sabaCan: 0,
		maguroCan: 0,
		chuuru: 0
	});

	setContext('clickCount', clickCount);
	setContext('items', items);

	onMount(() => {
		let currentRate = 0;
		const timer = setInterval(() => {
			clickCount.update((count) => count + currentRate / 4);
		}, 250);

		items.subscribe((item) => {
			currentRate = item.kariKari * 1 + item.sabaCan * 2 + item.maguroCan * 5 + item.chuuru * 10;
		});

		return () => {
			clearInterval(timer);
		};
	});
</script>

<slot />
