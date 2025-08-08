<script lang="ts">
	import { url } from '$lib/config';
	import { CirclePlay, CirclePause } from 'lucide-svelte';
	import CodeMirror from 'svelte-codemirror-editor';
	import { javascript } from '@codemirror/lang-javascript';
	import { cobalt } from 'thememirror';

	let { code, htmlPage = 'index.html', editor = true, autoplay = false, lines = null } = $props();

	let name = Math.random().toString(36).substring(2, 7);
	let theSketch = $state(code);

	let getUrlForReadyIframe = (theCode: string) => {
		return autoplay
			? getEntireUrlForIframe(theCode, htmlPage)
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

	let changed = (e) => {
		theSketch = e.detail;
		$inspect(theSketch);
	};
</script>

<div class="flex w-full flex-row flex-nowrap justify-center gap-10">
	{#if editor}
		<div class="mt-0 w-1/2 flex-initial pt-0 not-prose">
			<CodeMirror
				bind:value={theSketch}
				on:change={changed}
				lang={javascript()}
				theme={cobalt}
				class="text-sm text-left"
				styles={{
					'&': {
						height: '30rem'
					}
				}}
			/>
		</div>
	{/if}

	<div class={[editor ? 'w-1/2' : 'w-full', 'flex-initial', 'pt-3']}>
		{#if editor}
			<div class="bg-base-200 flex flex-row gap-5">
				<a class="btn" href={getEntireUrlForIframe(theSketch, htmlPage)} target={name}
					><CirclePlay /></a
				>
			</div>
		{/if}
		<iframe
			class="mt-2 h-[28rem] w-full bg-white"
			{name}
			title="p5 sketch"
			data-src={getUrlForReadyIframe(theSketch)}
			data-preload
		></iframe>
	</div>
</div>