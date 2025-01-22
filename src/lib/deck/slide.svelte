<script lang="ts">
	let { id = null, animate = false, restart = false, backgroundImage = null, url = null, children } = $props();


</script>

<section
	{id}
	data-auto-animate-id={id}
	data-auto-animate={animate || null}
	data-auto-animate-restart={restart || null}
	data-background-image={backgroundImage || null}
	data-background-opacity={backgroundImage ? 0.66 : null}
	data-background-iframe={url || null}
>
{@render children?.()}
</section>
