<script lang="ts">
	let { id = null, animate = false, restart = false, backgroundImage = null, children } = $props();


</script>

<section
	{id}
	data-auto-animate-id={id}
	data-auto-animate={animate || null}
	data-auto-animate-restart={restart || null}
	data-background-image={backgroundImage || null}
	data-background-opacity="0.66"
>
{@render children?.()}
</section>
