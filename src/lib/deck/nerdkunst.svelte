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
  createCanvas(500, 500);
    background(0);
  
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
  <P5 code={sketch} /> 
</Slide> 



<Slide>
  <h1>toedels</h1>>
  <p>hier komt veeeeeel text</p>
</Slide> 