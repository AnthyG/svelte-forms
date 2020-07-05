<script>
	import { form, bindClass } from "./../../src/index.js";

	let name = "";

	const myForm = form(() => ({
		name: { value: name, validators: ["required"] }
	}));
</script>

<style>
	:global(input.invalid) {
		border-color: red;
	}
</style>

<form>
	<input
		type="text"
		name="name"
		bind:value={name}
		use:bindClass={{ form: myForm }} />

	<button disabled={!$myForm.valid}>Login</button>
</form>
