<script lang="ts">
	export let title: string = '';
	export let subtitle: string = '';
	export let logo: string = 'assets/images/logo.jpg';
	export let logoAlt: string = 'Logo';
</script>

<header style="padding: 1rem; background-color: #34ab62; color: white;">
	<div>
		<h1>{title}</h1>
		{#if subtitle}
			<p style="opacity: 0.8;">{subtitle}</p>
		{/if}
	</div>
	<img src={logo} alt={logoAlt} width="70"height="50"/>
</header>

<style>
	header {
		display: flex;
		align-items: center;
		justify-content: space-between;
		padding: 1rem;
		background-color: #34ab62;
		color: white;
	}
	h1 {
		margin: 0;
	}
	p {
		margin: 0.25rem 0 0 0;
		font-weight: 300;
	}
</style>
