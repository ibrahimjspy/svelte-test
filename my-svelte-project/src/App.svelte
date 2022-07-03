<script>
	import axios from 'axios';
	import {onMount} from 'svelte';

	const requestAPI = async () => {
		const data = {};
		const call = await axios.get('https://catfact.ninja/fact').then(
			res => console.log(res.data)
		)
	};

	let firtname = "World";
	let second = " King";
	let count = 0;
	let cats = [
		{  name: 'Keyboard Cat' },
		{  name: 'Maru' },
		{  name: 'Henri The Existential Cat' }
	];
	const increment = () => {
		console.log(count)
		count = count + 1
	}
	$: name = firtname + "" + second
</script>

<main>
	<h1>Hello {name}! Ibrahim was here with {count} times</h1>
	<button on:click={increment}>State increment</button>
	<button on:click={requestAPI}>APi call</button>

	{#if count == 0}
		<p>First time</p>
	{/if}
	{#if count !== 0}
		<p>Not first time</p>
	{/if}
	{#each cats as cat}
		<p>{cat.name}</p>
	{/each}
</main>

<style>
	button{
		border-radius: 4px;
		box-shadow: inset;
		color: aqua;
		background-color:blueviolet ;
	}
	button:hover{
		color: black;
		background-color: white;
		transform: translateX(5px);
	}
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>