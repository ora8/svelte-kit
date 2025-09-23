<script lang="ts">
	let name = '';
	let email = '';
	let message = '';
	let submitted = false;
	let error = '';

	const handleSubmit = (event: Event) => {
		event.preventDefault();

		// Basic validation
		if (!name || !email || !message) {
			error = 'All fields are required.';
			return;
		}

		// You can handle form submission here (e.g., send data to a server)
		console.log({ name, email, message });
        window.location.href = createMail('urswag contact form submission', `Name: ${name}\nEmail: ${email}\nMessage: ${message}`);
		submitted = true; // Set submitted to true after successful submission
		error = ''; // Clear error message
   };

	function createMail(subject: string, body: string): string {
		const encodedSubject = encodeURIComponent(subject);
		const encodedBody = encodeURIComponent(body);
		return `mailto:urs.wagner.ch@gmx.ch?subject=${encodedSubject}&body=${encodedBody}`;
	}
</script>

<div class="form-container">
    {#if !submitted}
	<form on:submit={handleSubmit}>
		{#if error}
			<div class="error">{error}</div>
		{/if}
		{#if submitted}
			<div class="success">Thank you for your message!</div>
		{/if}
		<label>
			Name:
			<input type="text" bind:value={name} placeholder="Your Name" />
		</label>
		<label>
			Email:
			<input type="email" bind:value={email} placeholder="Your Email" />
		</label>
		<label>
			Message:
			<textarea bind:value={message} placeholder="Your Message"></textarea>
		</label>
		<div class="button-container">
			<button type="submit">Send</button>
		</div>
	</form>
{/if}
{#if submitted}
    <div class="success">Thank you for your message! I will get back to you soon.</div>
{/if}   
</div>

<style>
	.form-container {
		max-width: 600px;
		margin: 0 auto;
		padding: 20px;
		border: 1px solid #ccc;
		border-radius: 8px;
		box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
		background-color: #f9f9f9;
	}

	.error {
		color: red;
		margin-bottom: 10px;
	}

	.success {
		color: green;
		margin-bottom: 10px;
	}

	label {
		display: block;
		margin-bottom: 10px;
		font-weight: bold;
	}

	input,
	textarea {
		width: 100%;
		padding: 10px;
		margin-bottom: 15px;
		border: 1px solid #ccc;
		border-radius: 4px;
		box-sizing: border-box;
	}

	button {
		padding: 10px 15px;
		border: none;
		border-radius: 4px;
		background-color: #28a745;
		color: white;
		cursor: pointer;
		font-size: 16px;
	}

	button:hover {
		background-color: #218838;
	}

	.button-container {
		display: flex;
		justify-content: flex-end; /* Aligns the button to the right */
	}
</style>