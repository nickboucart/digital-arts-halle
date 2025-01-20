<script lang="ts">
    import { scale } from 'svelte/transition'
	import { url } from '$lib/config';
	import { CirclePlay, CirclePause, Code, Fullscreen } from 'lucide-svelte';
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

<div class="not-prose flex w-full flex-row justify-center gap-10">
	{#if editor}
<div transition:scale>
		<CodeMirror
        
			bind:value={code}
			lang={javascript()}
			theme={cobalt}
			class="not-prose w-full text-left text-base"
			styles={{
				'&': {
					height: '30rem'
				}
			}}
		/>
        </div>
	{/if}

	<div class="w-full"
        style:transition="transition: flex-grow 1000ms linear;">
		<iframe
			class="mt-2 h-[28rem] w-full bg-white"
			{name}
			title="p5 sketch"
			src={getUrlForReadyIframe()}
		></iframe>
		<div class="bg-base-200 flex flex-row justify-center gap-5">
			<a class="btn" href={getEntireUrlForIframe(code, htmlPage)} target={name}><CirclePlay /></a>
			<a class="btn" href={getUrlForReadyIframe()} target={name}><CirclePause /></a>
			<!-- svelte-ignore a11y_click_events_have_key_events -->
			<!-- svelte-ignore a11y_missing_attribute -->
			<!-- svelte-ignore a11y_no_static_element_interactions -->
			{#if editor}
				<a class="btn" onclick={() => {toggleEditor(false)}}><Fullscreen /></a>
			{:else}
				<a class="btn" onclick={() => {toggleEditor(true)}}><Code /></a>
			{/if}
		</div>
	</div>
</div>
