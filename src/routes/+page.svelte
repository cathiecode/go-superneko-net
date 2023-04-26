<script>
	import Clicker from './components/Clicker.svelte';
	import List from './components/List.svelte';
	import ListItem from './components/ListItem.svelte';
  import Store from './components/Store.svelte';
</script>

<div class="text-center">
	<Clicker className="mx-auto mt-8">
		<img
			class="w-auto h-24"
			src="/images/superneko.svg"
			alt="Illustration of a rainbow-colored cat"
		/>
	</Clicker>
</div>
<div class="text-center">
	<main class="inline-block mt-8 text-left p-8 rounded-md text-gray-300 bg-gray-800 shadow">
		<List>
			<ListItem href="/twitter">
				<i slot="icon" class="fa-brands fa-twitter" />
				<span slot="title">Twitter</span>
			</ListItem>
			<ListItem href="/github">
				<i slot="icon" class="fa-brands fa-github" />
				<span slot="title">GitHub</span>
			</ListItem>
			<ListItem href="https://superneko.net/">
				<img
					slot="icon"
					class="inline w-auto h-[1em] rounded-full bg-white"
					src="/images/superneko.svg"
					alt="Illustration of a rainbow-colored cat"
				/>
				<span slot="title">Super Neko</span>
			</ListItem>
      <Store />
		</List>
	</main>
</div>
