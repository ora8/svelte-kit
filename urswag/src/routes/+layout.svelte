<script lang="ts">
	import '../app.css';
	import favicon from '$lib/assets/favicon.svg';
	import logo from '$lib/assets/images/logo.jpg';
	import Header from '$lib/Header.svelte';;
	import Footer from '$lib/Footer.svelte';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<Header title="Urs Wagner" subtitle="Software Developer" 
	logo={logo} />

{@render children?.()}


<Footer/>

<style>

</style>