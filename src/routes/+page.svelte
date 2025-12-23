<script lang="ts">
	import Header from "$lib/components/Header.svelte";

	let state = $state(false);
	const changeState = () => {
		state = !state;
	};
</script>


<Header />
<h1>Main Page</h1>

<div class={`a ${state ? '' : ''}`}>
	a
</div>
<div class={['b', {'replace': state}]}>
	b
</div>

<button onclick={changeState}>Change State ({state})</button>

<style>
	:global(body) {
		min-height: 200vh;
	}


	h1 {
		color: white;
		font-size: 3em;
		text-align: center;
		margin-top: 2rem;
	}
	button {
		margin-top: 2rem;
		padding: 0.5rem 1rem;
		font-size: 1rem;
		background-color: white;
		cursor: pointer;
	}

	.a {
		width: 100px;
		height: 100px;
		background-color: white;
	}
	.b {
		width: 100px;
		height: 100px;
		background-color: grey;
	}

	.replace {
		background-color: yellow;
	}
</style>


