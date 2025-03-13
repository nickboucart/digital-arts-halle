<script lang="ts">
	import { onMount } from 'svelte'

	import Reveal from 'reveal.js'
	import Highlight from 'reveal.js/plugin/highlight/highlight'
	import Markdown from 'reveal.js/plugin/markdown/markdown'
	import Notes from 'reveal.js/plugin/notes/notes'

	import 'reveal.js/dist/reveal.css'
	import 'reveal.js/dist/theme/night.css'
	import 'reveal.js/plugin/highlight/monokai.css'

	let { children, autoSlide = 0 } = $props();

	onMount(() => {
		const deck = new Reveal({
			plugins: [Markdown, Highlight, Notes],
			autoAnimateEasing: 'ease',
			autoAnimateDuration: 1,
			hash: false,
			autoSlide,
			loop: true,
			viewDistance: 2,
			// disableLayout: true
			controls: false,
			// progress: false
		})

		deck.initialize()
	})
</script>

<div class="reveal">
	<div class="slides">
		{@render children?.()}
	</div>
</div>
