<script lang="ts">
    import { scale } from 'svelte/transition'
	import { url } from '$lib/config';
	import CodeBlock from '$lib/deck/code.svelte';
	import CodeMirror from 'svelte-codemirror-editor';
	import { javascript } from '@codemirror/lang-javascript';
	import { cobalt } from 'thememirror';

	let { code, htmlPage = 'index.html', editor = true, autoplay = false } = $props();

	let name = Math.random().toString(36).substring(2, 7);

	let getUrlForReadyIframe = () => {
		return autoplay
			? getEntireUrlForIframe(code, htmlPage)
			: new URL('/p5/ready/index.html', url).toString();
	};

	let getPauzeUrlForIframe = () => {
		return new URL('/p5/ready/index.html', url).toString();
	};

	let getEntireUrlForIframe = (sketch: string, html: string) => {
		let urlForSketch = new URL('/p5/' + html, url);
		urlForSketch.searchParams.set('sketch', sketch);
		return urlForSketch.toString();
	};

	let toggleEditor = (toggle: boolean) => {
		if (toggle) {
			editor = true;
		} else {
			editor = false;
		}
	};
</script>

<div class="not-prose flex w-full flex-row flex-nowrap justify-center gap-10">
	{#if editor}
<div class="w-1/2 flex-initial pt-0 mt-0">
		<CodeBlock code={code} />
        </div>
	{/if}

	<div class={[editor ? "w-1/2" : "w-full", "flex-initial", "pt-3"]}>
		<iframe
			class="mt-2 h-[28rem] w-full bg-white"
			{name}
			title="p5 sketch"
			data-src={getUrlForReadyIframe()}
			data-preload
		></iframe>
	</div>
</div>
