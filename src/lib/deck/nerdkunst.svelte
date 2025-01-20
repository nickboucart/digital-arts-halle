<script lang="ts">
	import Slide from './slide.svelte'
	import Code from './code.svelte'
	import Markdown from './markdown.svelte'
	import Notes from './notes.svelte'
	import P5 from '$lib/components/P5.svelte'

	let sketch = `const size = 15;
let x = 0;
let y = 0;

function setup() {
  createCanvas(500, 400);
    background("#111111");
  
  }

function draw() {
  fill(230);
  stroke('white')
  strokeWeight(2);

      if (random(1) < 0.5) {
      line(x,y, x+size, y+size);
      }
      else {
        line(x, y+size, x+size, y);
      }
  x = x + size;
  if (x > width ) {
    x = 0;
    y = y + size;
  }
  if (y > height) {
    noLoop();
  }
}`

import vierkanten from "$lib/assets/vierkanten.png"
</script>





<Slide backgroundImage={vierkanten}>
	<!-- todo: background image van de site en veel betere styling van tekst -->
	<h1 class="text-black">NerdKunst</h1>
	<p>Omdat wetenschap en technologie soms ook gewoon mooi kunnen zijn.</p>
</Slide>

<Slide>
  <P5 code={sketch} editor={false} autoplay={true} /> 
</Slide> 


<Slide>
  <h2>Famous one liner</h2>
 <Code>
  10 PRINT CHR$(205.5+RND(1)); : GOTO 10
 </Code>
 <Notes>
  <p>early 80's commodore 64  focus on single line programs, this is one of the most famous ones, and an excellent example of generative art</p>
 </Notes>
</Slide> 