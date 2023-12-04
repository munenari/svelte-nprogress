<script lang="ts">
	import NProgress from 'nprogress'
	import 'nprogress/nprogress.css'

	export let opts: Partial<NProgress.NProgressOptions> = {
		showSpinner: false
	}
	export let isNavigating: boolean = false
	export let color: string = '#f0d'

	NProgress.configure(opts)
	$: {
		if (isNavigating) {
			NProgress.start()
		}
		if (!isNavigating) {
			NProgress.done()
		}
	}
	$: changeColor(color)
	function changeColor(c: string) {
		if (typeof document === 'undefined') return
		const el = document.querySelector(':root') as HTMLElement
		el?.style.setProperty('--nprogress-color', c)
	}
	export function getInstance(): NProgress.NProgress {
		return NProgress
	}
</script>

<style>
	:root {
		--nprogress-color-default: #f0d;
	}
	:global(#nprogress .bar) {
		background: var(--nprogress-color, var(--nprogress-color-default));
	}
	:global(#nprogress .peg) {
		box-shadow:
			0 0 10px var(--nprogress-color, var(--nprogress-color-default)),
			0 0 5px var(--nprogress-color, var(--nprogress-color-default));
	}
	:global(#nprogress .spinner-icon) {
		border-top-color: var(--nprogress-color, var(--nprogress-color-default));
		border-left-color: var(--nprogress-color, var(--nprogress-color-default));
	}
</style>
