# nprogress in svelte

## refer https://github.com/rstacruz/nprogress

## usage

```bash
$ npm install --save-dev svelte-nprogress
```

- in `+layout.svelte`

```svelte
<script lang="ts">
	import NProgress from 'svelte-nprogress'
	import { navigating } from '$app/stores'
	let color = 'red' // or #f00
</script>

<NProgress isNavigating={Boolean($navigating)} {color}></NProgress>

```
