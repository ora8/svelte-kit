<script lang="ts">
	import { goto } from '$app/navigation';
	import Button from '$components/Button.svelte';

	function handleClick() {
		console.log('Button clicked');
		goto('/contact');
	}
</script>

<section class="main-section default-margin">
	<h1>Hello I'm Urs</h1>
	<div class="underscore mb-m"></div>
	<h1>I'm a Software Developer of C++, C, C#, Svelte.</h1>
	<Button onClick={handleClick}>Contact me</Button>
</section>
