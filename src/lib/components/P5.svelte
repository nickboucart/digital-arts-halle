<script lang="ts">
    import { url } from '$lib/config'
    import { CirclePlay, CirclePause} from 'lucide-svelte';
    import CodeMirror from "svelte-codemirror-editor";
    import { javascript } from "@codemirror/lang-javascript";
    import { cobalt } from "thememirror";

  
    export let code: string;
    export let htmlPage: string = "index.html";
    let name = Math.random().toString(36).substring(2,7);

    let getUrlForReadyIframe = () => {
        return new URL('/p5/ready/index.html', url).toString();
    }


    let getEntireUrlForIframe = (sketch: string, html: string) => {
        let urlForSketch = new URL('/p5/' + html, url)
        urlForSketch.searchParams.set('sketch', sketch)
        return urlForSketch.toString()
    }

    
</script>


<div class="grid grid-cols-1 lg:grid-cols-2 justify-center content-evenly not-prose gap-4 w-full">	
    <CodeMirror bind:value={code} lang={javascript()} theme={cobalt} class="not-prose text-base text-left" styles={{
        "&": {
            height: "30rem",
        },
    }}/>
    <div>
        <div class="flex flex-row gap-5 bg-base-200">
            <a class="btn" href="{getEntireUrlForIframe(code, htmlPage)}" target={name}><CirclePlay /></a>
            <a class="btn" href="{getUrlForReadyIframe()}" target={name}><CirclePause /></a>
        </div>
    <iframe class="mt-2 w-full h-[28rem] bg-white" {name} title="p5 sketch" src={getUrlForReadyIframe()}></iframe>
</div>
</div>