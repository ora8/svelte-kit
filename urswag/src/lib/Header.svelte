<script lang="ts">
	export let title: string = '';
	export let subtitle: string = '';
	export let logo: string = 'assets/images/logo.jpg';
	export let logoAlt: string = 'Logo';
</script>

<header>
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
    background-color: #34ab62; /* Header color */
    color: white; /* Header text color */
	margin: 0rem 10rem;
	padding: 0.5rem 1rem;
  }
  	p {
		margin: 0.25rem 0 0 0;
		font-weight: 300;
	}

</style>
