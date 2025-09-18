<script>
	import Canvas from "$components/Canvas.svelte";
	import Clock from "$components/Clock.svelte";
	import MainSection from "$components/sections/MainSection.svelte";

</script>

<nav>
    <a href="/">Home</a>
    <a href="/arduino">Arduino</a>
    <a href="/about">About</a>
</nav>

<MainSection/>

<Clock width={500} height={400} background="#f0f0f0" />