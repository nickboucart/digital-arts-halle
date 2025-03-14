<script lang="ts">
	let { id = null, lines = null, noescape = true, code } = $props();
</script>

<div class="w-full text-left text-2xl mt-0 pt-0">
	<pre data-id={id || null}><code
			class="language-javascript"
			data-trim
			data-line-numbers={lines || true}
			data-noescape={noescape || null}>{code}</code>
</pre>
</div>
