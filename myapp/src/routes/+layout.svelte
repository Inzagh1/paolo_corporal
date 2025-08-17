<script>
	import '../app.css';
	import favicon from '$lib/assets/favicon.svg';

	import Footer from '$lib/components/footer.svelte';
	

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href="/logo.png" />
</svelte:head>

{@render children?.()}

<div class="">
	<Footer />
</div>