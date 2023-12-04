<script lang="ts">
	import NProgress from '$lib/NProgress.svelte'
	import { navigating } from '$app/stores'
</script>

<NProgress isNavigating={Boolean($navigating)} color='blue'></NProgress>

<p>navigation</p>
<header class='row'>
	<a href='/foo'>foo</a>
	<a href='/bar'>bar</a>
</header>
<div>
	<slot />
</div>
<footer class='row'>
	<a href='/'>index</a>
</footer>

<style>
	.row {
		display: flex;
		gap: 0.5em;
	}
</style>
