<script>
	import MainSection from "$components/sections/MainSection.svelte";

</script>

<div class="nav-container">
<nav>
    <a href="/">Home</a>
    <a href="/arduino">Arduino</a>
    <a href="/about">About</a>
</nav>
</div>

<MainSection/>

<style>
 .nav-container {
    display: flex; /* Enable flexbox */
    justify-content: flex-end; /* Align children to the right */
    padding: 1rem; /* Optional: Add some padding */
  }
</style>