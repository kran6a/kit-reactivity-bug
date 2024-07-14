<script lang="ts">
	import {onMount} from "svelte";

	const {data}: {data: PageData} = $props();
	onMount(()=>{
		const interval = setInterval(()=>{
			const new_element = data.items.at(-1)+1;
			console.log(`Pushing ${new_element} to data.items`);
			data.items.push(new_element)
		}, 1000);
		return ()=>clearInterval(interval);
	})
</script>

{#each data.items as i}
	<p>{i}</p>
{/each}
