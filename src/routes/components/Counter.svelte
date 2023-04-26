<script lang="ts">
	import { onMount } from 'svelte';
	import { writable } from 'svelte/store';

	export let count: number;

	let currentCount = writable(count);

	onMount(() => {
		let frame: number;
		let timer: number = performance.now();
		function loop(currentTime: number) {
      currentCount.update(c => c * 0.95 + count * 0.05);

      timer = currentTime;
			frame = requestAnimationFrame(loop);
		}

    loop(timer);

		return () => cancelAnimationFrame(frame);
	});
</script>
{Math.round($currentCount)}
