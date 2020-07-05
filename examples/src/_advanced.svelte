<script>
	import { form } from "./../../src/index.js";

	let name = "";
	let email = "";

	const usernameIsNotTaken = async value =>
		fetch(`https://jsonplaceholder.typicode.com/users?username=${value}`)
			.then(d => d.json())
			.then(d => ({
				name: "usernameIsNotTaken",
				valid: !d.length
			}));

	const loginForm = form(
		() => ({
			name: {
				value: name,
				validators: ["required", "min:6", usernameIsNotTaken]
			},
			email: { value: email, validators: ["required", "email"] }
		}),
		{
			initCheck: true,
			validateOnChange: false,
			stopAtFirstError: false,
			stopAtFirstFieldError: false
		}
	);
</script>

<form>
	<input type="text" bind:value={name} />

	{#if $loginForm.fields.name.errors.includes('required')}
		<p>The name is required</p>
	{/if}

	{#if $loginForm.fields.name.errors.includes('min')}
		<p>The name should be at least 6 characters</p>
	{/if}

	{#if $loginForm.fields.name.pending}
		<p>Checking name availability..</p>
	{/if}

	{#if $loginForm.fields.name.errors.includes('usernameIsNotTaken')}
		<p>This username is already taken</p>
	{/if}

	<input
		type="email"
		bind:value={email}
		class:valid={$loginForm.fields.email.valid} />

	{#if $loginForm.fields.email.errors.includes('email')}
		<p>The email is invalid</p>
	{/if}

	<button on:click|preventDefault={() => loginForm.validate()}>
		Validate form
	</button>
	<button disabled={!$loginForm.valid}>Login</button>
</form>
