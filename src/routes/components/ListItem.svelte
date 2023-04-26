<script lang="ts">
	export let href: string = "#";
  export let className = "";
</script>

<a class={`table-row ${className}`} on:click {href}>
	<div class="table-cell pb-2 pe-4">
		<slot name="icon" />
	</div>
	<div class="table-cell py-2">
		<slot name="title" />
	</div>
</a>
