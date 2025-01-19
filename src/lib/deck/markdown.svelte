<script lang="ts">

	let {name = 'example.md', external=false, children } = $props()
</script>

{#if external}
	<section data-markdown={name} ></section>
{:else}
	<section data-markdown>
		<div data-template>
			{@render children?.()}
		</div>
	</section>
{/if}
