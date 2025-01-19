<script lang="ts">
	import Slides from '$lib/deck/slides.svelte'
	import Presentation from '$lib/deck/nerdkunst.svelte'
	import '../app.postcss'

</script>

<svelte:head>
	<title>NerdKunst</title>
</svelte:head>

<Slides>
	<Presentation />
</Slides>
