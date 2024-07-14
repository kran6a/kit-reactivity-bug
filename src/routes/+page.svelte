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

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section>
	{#each data.items as i}
		<p>{i}</p>
	{/each}
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
	}

	h1 {
		width: 100%;
	}

	.welcome {
		display: block;
		position: relative;
		width: 100%;
		height: 0;
		padding: 0 0 calc(100% * 495 / 2048) 0;
	}

	.welcome img {
		position: absolute;
		width: 100%;
		height: 100%;
		top: 0;
		display: block;
	}
</style>
