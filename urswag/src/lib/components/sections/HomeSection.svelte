<script lang="ts">
	import Button from '$components/Button.svelte';
	import Clock from '$components/Clock.svelte';

</script>

<section class="main-section default-margin">
	<h1>Hello I'm Urs</h1>
	<div class="underscore mb-m"></div>
	<h1>I'm a Software Developer of C++, C, C#, Svelte.</h1>
	<a href="/contact">
	<Button>Feel free, to contact me</Button>
	</a>
	<div class="clock-container">
	<div class="clock-wrapper">
	<Clock size={500} background="#f0f0f0" />
	</div>
	</div>
</section>

<style>
  .clock-container {
    display: flex; /* Enable flexbox */
    justify-content: flex-end; /* Align children to the right */
    padding: 1rem; /* Optional: Add some padding */
  }

  .clock-wrapper {
    margin-right: 2rem; /* Space from the right edge */
  }
</style>