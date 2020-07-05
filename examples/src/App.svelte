<script>
	import Basic from "./_basic.svelte";
	import Advanced from "./_advanced.svelte";
</script>

<style>
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

	.form {
		width: 100%;
		margin: 0 auto;
		padding: 12px 0;
		margin-bottom: 24px;
		border: 1px solid black;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>

<main>
	<h1>svelte-forms Examples</h1>

	<div class="form">
		<h2>Basic</h2>
		<Basic />
	</div>

	<div class="form">
		<h2>Advanced</h2>
		<Advanced />
	</div>
</main>
