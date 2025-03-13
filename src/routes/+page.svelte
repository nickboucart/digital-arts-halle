<script lang="ts">
	import Slides from '$lib/deck/slides.svelte'
	import Presentation from '$lib/deck/digital-arts-halle.svelte'
	import '../app.postcss'

</script>

<svelte:head>
	<title>NerdKunst</title>
</svelte:head>

<Slides autoSlide={8000}>
	<Presentation />
</Slides> 
