<script lang="ts">
	import favicon from '$lib/assets/images/favicon-32x32.png';
	import '@fontsource/league-spartan/300.css';
	import '@fontsource/league-spartan/400.css';
	import '@fontsource/league-spartan/500.css';
	import '../app.css';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

{@render children()}
