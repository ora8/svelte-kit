<script lang="ts">
	import Button from '$components/Button.svelte';
	import Clock from '$components/Clock.svelte';
	import intro from '$lib/assets/images/intro.jpg';
	let introAlt = 'Intro';
</script>

<section class="main-section">
	<div class="main-container">
		<div class="info-container">
			<h1>Hello I'm Urs</h1>
			<div class="underscore mb-m"></div>
			<h1>I'm a Software Developer using C++, C, C#, Svelte.</h1>
			<br />
			<a href="/contact"><Button>Feel free, to contact me</Button></a>
			<img src={intro} alt={introAlt} class="intro-container" width="300" height="200" />
		</div>
		<div class="clock-container">
			<div class="clock-wrapper">
				<Clock size={500} background="#f0f0f0" />
			</div>
		</div>
	</div>
</section>

<style>
	.clock-container {
		position: absolute; /* Position the second child absolutely */
		margin: 5rem;
		right: 0; /* Align it to the right */
		width: 30%; /* Adjust width as needed */
	}

	.clock-wrapper {
		margin-right: 2rem; /* Space from the right edge */
	}

	.info-container {
		float: left;
		width: 60%;
	}

	.intro-container {
		margin-top: 3rem;
	}

</style>
