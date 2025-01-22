<script lang="ts">
    import P5 from '$lib/components/P5.svelte'
	let sketch = `
const size = 15;
let x = 0;
let y = 0;

function setup() {
  createCanvas(400, 400);
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
</script>

<svelte:head>
	<title>NerdKunst</title>
</svelte:head>

<P5 code={sketch} /> 
