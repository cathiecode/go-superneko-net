<script>
	import StoreItem from './StoreItem.svelte';
</script>

<StoreItem name="Karikari" id="kariKari" price={10} rate={1}>
  <i slot="icon" class="fa-solid fa-bowl-food"></i>
</StoreItem>
<StoreItem name="Saba can" id="sabaCan" price={50} rate={2}>
  <i slot="icon" class="fa-solid fa-fish"></i>
</StoreItem>
<StoreItem name="Maguro can" id="maguroCan" price={100} rate={5}>
  <i slot="icon" class="fa-solid fa-fish-fins"></i>
</StoreItem>
<StoreItem name="Chuuru" id="chuuru" price={300} rate={10}>
  <i slot="icon" class="fa-solid fa-wand-magic-sparkles"></i>
</StoreItem>
