<script lang="ts">
	import Slide from './slide.svelte'
	import Code from './code.svelte'
	import Markdown from './markdown.svelte'
	import Notes from './notes.svelte'
	import P5 from '$lib/components/P5.svelte'
  import Strudel from '$lib/components/Strudel.svelte'

	let print10 = `const size = 15;
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

let print10bis = `const size = 15;
const cutoff = 0.5;

function setup() {
  createCanvas(500, 400);
  background("#111111");
  noLoop();
}

function draw() {
  fill(230);
  stroke("white");
  strokeWeight(2);
  for (let x = 0; x < width; x += size) {
    for (let y = 0; y < height; y += size) {
      if (random(1) < cutoff) {
        line(x, y, x + size, y + size);
      } else {
        line(x, y + size, x + size, y);
      }
    }
  }
}`

let boilerplate = `let pos;
let vel;

function setup() {
  createCanvas(100, 100);
  // Create p5.Vector objects.
  pos = createVector(50, 100);
  vel = createVector(0, -1);
}

function draw() {
  background(200);
  // Add velocity to position.
  pos.add(vel);
  // If the dot reaches the top of the canvas,
  // restart from the bottom.
  if (pos.y < 0) {
    pos.y = 100;
  }
  // Draw the dot.
  strokeWeight(5);
  point(pos);
}`

let lines1 = `let l = 30;

function setup() {
  createCanvas(400, 400);
  background(230);
  let aantalStreepjesPerLijn = width / l;
  noFill();
  for (x = 0; x < aantalStreepjesPerLijn; x++) {
    for (y = 0; y < aantalStreepjesPerLijn; y++) {
    stroke(0);
     //rect(x * l, y * l, l);
      if (y % 2 == 0 ) { // een even rij, dus horizontaal streepje
        line(x * l, y * l + l / 2,  x*l + l, y * l + l / 2);
      }
      else {
        line(x * l+l/2, y * l,  x * l+l/2, y * l + l);
      }
    }
  }
}

function draw() {}`

let lines2 = `let l = 20;
let hoek;

function setup() {
  createCanvas(400, 400);
  background(230);
  angleMode(DEGREES);
  hoek = random(0, 180);
  let aantalStreepjesPerLijn = width / l;
  noFill();
  for (x = 0; x < aantalStreepjesPerLijn; x++) {
    for (y = 0; y < aantalStreepjesPerLijn; y++) {
      stroke(0);
      if (y % 2 == 0) {
        push();
        translate(
          x * l + l / 2,
          y * l + l / 2
        );
        rotate(hoek);
        line(-l/2,0,l/2,0);
        pop();
      } else {
        push();
        translate(x * l + l / 2,y * l + l / 2
        );
        rotate(hoek);
        line(0, -l / 2, 0, l / 2);
        pop();
      }
    }
  }
}

function draw() {}`

let squares1= `let vierkantenPerRij = 25;
let canvas = 450;

function setup() {
  createCanvas(canvas, canvas);
  rectMode(CENTER);
  background(0);
  stroke(255);

  let grootteVierkant = canvas / vierkantenPerRij;
  for (var x = 0; x < vierkantenPerRij; x += 1) {
    for (var y = 0; y < vierkantenPerRij; y += 1) {
      let rood = random(0,255);
      let groen = random(0,255);
      let blauw = random(0,255);
      fill(rood, groen, blauw);
      square(
        x * grootteVierkant + grootteVierkant / 2,
        y * grootteVierkant + grootteVierkant / 2,
        grootteVierkant
      );
    }
  }
}

function draw() {};`

let squares2 = `let vierkantenPerRij = 25;
let canvas = 450;
let variatie = 0.4; //hoe groter dit getal, hoe groter de variatie

function setup() {
  createCanvas(canvas, canvas);
  rectMode(CENTER);
  background(0);
  stroke(255);
  //noStroke();

  let grootteVierkant = canvas / vierkantenPerRij;
  for (var x = 0; x < vierkantenPerRij; x += 1) {
    for (var y = 0; y < vierkantenPerRij; y += 1) {
      let kleur = floor(map(noise(x*variatie, y*variatie), 0,1,0,255));
      fill(kleur);
      square(
        x * grootteVierkant + grootteVierkant / 2,
        y * grootteVierkant + grootteVierkant / 2,
        grootteVierkant
      );
    }
  }
}

function draw() {};`

let squares3 = `let vierkantenPerRij = 25;
let canvas = 450;
let variatie = 0.4; //hoe groter dit getal, hoe groter de variatie

function setup() {
  createCanvas(canvas, canvas);
  rectMode(CENTER);
  background(0);
  stroke(255);
  //noStroke();
  let rood = floor(random(0,255));
  let blauw = floor(random(0,255));

  let grootteVierkant = canvas / vierkantenPerRij;
  for (var x = 0; x < vierkantenPerRij; x += 1) {
    for (var y = 0; y < vierkantenPerRij; y += 1) {
      let groen = floor(map(noise(x*variatie, y*variatie), 0,1,0,255));
      fill(rood, groen, blauw);
      square(
        x * grootteVierkant + grootteVierkant / 2,
        y * grootteVierkant + grootteVierkant / 2,
        grootteVierkant
      );
    }
  }
}

function draw() {};`

let landscape = `let zoom = 0.01;

let water;
let zand;
let gras;
let bos;

function setup() {
  colorMode(RGB);
  createCanvas(500, 500);
  zand = color(215, 192, 158);
  water = color(30, 176, 251);
  bos = color(2, 166, 155);
  gras = color(22, 181, 141);
  // we laden alle pixels in geheugen.
  loadPixels();
  noLoop();
}

function draw() {
  background(220);
  for (let x = 0; x < width; x++) {
    for (let y = 0; y < height; y++) {
      // noise geeft getal tussen 0 en 1, dat we omzetten naar een grijswaarde tussen 0 en 255
      let kleur = noise(x * zoom, y * zoom);
      if (kleur < 0.3) {
        set(x, y, water);
      } else if (kleur < 0.4) {
        set(x, y, zand);
      } else if (kleur < 0.6) {
        set(x, y, gras);
      } else {
        set(x, y, bos);
      }
    }
  }
  updatePixels();
}`

let sine1 = `let straal = 125;
let hoek = 30;

function setup() {
  angleMode(DEGREES);
  createCanvas(400, 400);
  background(255);
  // maak de oorsprong gelijk aan het midden van het canvas
  translate(width / 2, height / 2);
  // dit draait de y-as, die in standaard p5js van boven naar beneden loopt, zodat die nu van beneden naar boven loopt
  scale(1, -1);
  noFill();
  circle(0, 0, 2 * straal);
  line(-width / 2, 0, width / 2, 0);
  line(0, -height / 2, 0, height / 2);
  fill("black");
  circle(1, 0, 1);
  circle(0, 1, 1);

  let x = straal * cos(hoek);
  let y = straal * sin(hoek);

  circle(x, y, 5);
  fill(230);
  line(0, 0, x, y);
  arc(0, 0, 100, 100, 0, 30);
  
  strokeWeight(2);
  stroke("green");
  line(0, y, x, y);
  stroke("blue");
  line(x, 0, x, y);


  // beetje prutsen om de teksten niet ondersteboven en op de juiste plaats te krijgen
  push();
  fill("black");
  stroke("black");
  strokeWeight(0.8);
  scale(1, -1);
  text("(0,0)", 10, 20);
  text(" (125, 0)", 125, -10);
  text(" (0, 125)", 10, -125);
  stroke("green");
  text("straal*cos(α)", 25, -70);
  stroke("blue");
  text("straal*sin(α)", 130, -35);
  stroke("black");
  textSize(20);
  text("x-as", width / 2 - 50, 20);
  text("y-as", 10, -height / 2 + 50);
  text("α", 50 * cos(-hoek / 2), 50 * sin(-hoek / 2));
  pop();
}`

let sine2 = `let straal = 125;
let hoek = 0;

function setup() {
  angleMode(DEGREES);
  createCanvas(400, 400);

}

function draw() {
  background(255);
  // maak de oorsprong gelijk aan het midden van het canvas
  translate(width / 2, height / 2);
  // dit draait de y-as, die in standaard p5js van boven naar beneden loopt, zodat die nu van beneden naar boven loopt
  scale(1, -1);
  noFill();
  circle(0, 0, 2 * straal);
  line(-width / 2, 0, width / 2, 0);
  line(0, -height / 2, 0, height / 2);
  fill("black");
  circle(1, 0, 1);
  circle(0, 1, 1);

  let x = straal * cos(hoek);
  let y = straal * sin(hoek);

  circle(x, y, 5);
  fill(230);
  line(0, 0, x, y);
  arc(0, 0, 100, 100, 0, hoek);
  
  push();
  strokeWeight(4);
  stroke("green");
  line(0, straal, x, straal);
  stroke("blue");
  line(straal, 0, straal, y);
  drawingContext.setLineDash([5,5]);
  strokeWeight(1);
  line(x,y, straal, y);
  stroke("green");
  line(x,y, x, straal);
  pop();
  
  hoek += 1;
}`

let knots = `let straal = 125;

function setup() {
  createCanvas(400, 400);
  background(220);
  colorMode(HSL);
}

function draw() {
  translate(width / 2, height / 2);

  let x = straal * cos(frameCount / 45);
  let y = straal * sin(frameCount / 20);

  noStroke();
  fill(frameCount % 360, 75, 50);
  circle(x, y, 10);
}`

let steam = `let video;
let pose;
let bodyPose;

function preload() {
  // Load the bodyPose model
  bodyPose = ml5.bodyPose();
}

class Deeltje {
  constructor(x, y, zijwind) {
    this.x = x;
    this.y = y;
    this.vy = -2;
    this.vx = zijwind + random(-0.5, 0.5);
    this.kleur = random(200,230);
    this.alpha = 255;
    this.straal = 5;
  }
  update() {
    this.y += this.vy;
    this.x += this.vx;
    this.alpha -= 3;
    this.straal += 1;
  }
  show() {
    noStroke();
    fill(this.kleur, this.alpha);
    ellipse(this.x, this.y, this.straal);
  }
}

function setup() {
  createCanvas(640, 480);
  deeltjes = [];
  video = createCapture(VIDEO);
  video.hide();
  bodyPose.detectStart(video, gotPoses);
}

function gotPoses(poses) {
  // poseNet kan poses van meerdere mensen op een beeld herkennen. We gebruiken enkel de eerste persoon
  if (poses.length > 0) {
    pose = poses[0];
  }
}

function draw() {
  background(0);
  image(video, 0, 0);

  if (pose) {
    let linkerOor = pose.left_ear;
    let rechterOor = pose.right_ear;
    let deeltje = new Deeltje(linkerOor.x, linkerOor.y, 1);
    deeltjes.push(deeltje);
    deeltje = new Deeltje(rechterOor.x, rechterOor.y, -1);
    deeltjes.push(deeltje);
  }
  for (i = 0; i < deeltjes.length; i++) {
    deeltjes[i].show();
    deeltjes[i].update();
  }
}`

import vierkanten from "$lib/assets/vierkanten.png"
import veramolnar from "$lib/assets/vera-molnar.jpg"
import molnar1 from "$lib/assets/molnar1.webp";
import molnar2 from "$lib/assets/molnar2.jpg";
import molnar3 from "$lib/assets/molnar3.webp";
import haroldcohen from "$lib/assets/harold-cohen.webp";
import cohen1 from "$lib/assets/cohen1.webp";
import caseyreas from "$lib/assets/Casey-Reas.jpg";
import reas1 from "$lib/assets/reas1.webp";
import reas2 from "$lib/assets/reas2.webp";
import rafaellozano from "$lib/assets/Rafael_Lozano-Hemmer.jpg";
import rafael1 from "$lib/assets/hemmer1.avif";
import turtle from "$lib/assets/turtle.png";
import gonio from "$lib/assets/gonio.png";
</script>





<Slide backgroundImage={vierkanten}>
	<!-- todo: background image van de site en veel betere styling van tekst -->
	<h1 class="text-black">NerdKunst</h1>
	<p>Omdat wetenschap en technologie soms ook gewoon mooi kunnen zijn.</p>
  <p class="text-right text-xl">Nick Boucart - nerdkunst.be</p>
</Slide>

<Slide>
  <h3>Famous one liner: 10 PRINT</h3>
 <Code>
  10 PRINT CHR$(205.5+RND(1)); : GOTO 10
 </Code>
 <Notes>
  early 80's commodore 64  focus on single line programs, this is one of the most famous ones, and an excellent example of generative art
 </Notes>
</Slide> 

<Slide>
  <P5 code={print10} editor={false} autoplay={true} /> 
</Slide> 

<Slide>
  <h3>Express yourselve through code</h3>
  <ul style="list-style-type: none;" class="r-stack">
    <li class="fragment fade-in-then-out">Visual - show, don't tell</li>
    <li class="fragment fade-in-then-out">Fun way to explore programming and Algorithms</li>
    <li class="fragment fade-in-then-out">Combo of (computer) science and art</li>
    <li class="fragment fade-in-then-out">Educational and interactive</li>
    <li class="fragment fade-in-then-out">Super fun to fiddle with parameters and see result</li>
  </ul>
  <p class="fragment fade-in text-right">Works for me &#128513;</p>
  </Slide>

<Slide>
<blockquote class="text-justify text-base"><span class="font-semibold">Generative art</span> is post-conceptual art that has been created (in whole or in part) with the use of an autonomous system. An autonomous system in this context is generally one that is non-human and can independently determine features of an artwork that would otherwise require decisions made directly by the artist. In some cases the human creator may claim that the generative system represents their own artistic idea, and in others that the system takes on the role of the creator. </blockquote>
<p class="font-light text-sm text-right">Wikipedia</p>
</Slide> 


<Slide>
<h3>Generative Art Pioneers</h3>
</Slide>

<Slide backgroundImage={veramolnar}>
  <h3>Vera Molnár (1924-2023)</h3>
  <Notes>
    <p>Swiss-Hungarian artist, pioneer in computer art, worked with algorithms and randomness</p>
    </Notes>
  </Slide>

<Slide backgroundImage={molnar1}></Slide>
<Slide backgroundImage={molnar2}></Slide>
<Slide backgroundImage={molnar3}></Slide>

<Slide backgroundImage={haroldcohen}>
  <h3>Harold Cohen (1928-2016)</h3>
  <Notes>
    <p>arold Cohen (1 May 1928 – 27 April 2016)[1] was a British-born artist who was noted as the creator of AARON,[2] a computer program designed to produce paintings and drawings autonomously, which set it apart from previous programs.[3] His work in the intersection of computer artificial intelligence and painting lead to exhibitions at many museums, including the Tate Gallery in London.[4]</p>
    </Notes>
  </Slide>
  <Slide backgroundImage={cohen1}></Slide>

  <Slide backgroundImage={caseyreas}>
    <h3>Casey Reas (1972)</h3>
    <Notes>
      <p>Casey Edwin Barker Reas (born 1972), also known as C. E. B. Reas or Casey Reas,[1] is an American artist whose conceptual, procedural and minimal artworks explore ideas through the contemporary lens of software. Reas is perhaps best known for having created, with Ben Fry, the Processing programming language.[2] MIT media lab.</p>
      </Notes>
    </Slide>

    <Slide backgroundImage={reas1}></Slide>
    <Slide backgroundImage={reas2}></Slide>

    <Slide backgroundImage={rafaellozano}>
      <h3>Rafael Lozano-Hemmer  (1967)</h3>
      <Notes>
        <p>Rafael Lozano-Hemmer RCA (born 1967 in Mexico City) is a Mexican-Canadian electronic artist living and working in Montreal, Quebec, Canada. He creates platforms for public participation by using robotic lights, digital fountains, computerized surveillance, and telematic networks. Inspired by phantasmagoria, carnival, and animatronics, his interactive works are “anti-monuments for people to self-represent.” Installaties, interactief, soms ook wat activistisch</p>
        </Notes>
      </Slide>
  
      <Slide backgroundImage={rafael1}></Slide>

<Slide>
  <h3>Generative AI-rtist</h3>
  <div class="flex flex-row justify-center gap-5">
    <blockquote class="w-full>">Generate an image for a tattoo design of a turtle carrying the world in a cute animal style, analyical cubism, glow in the dark colors</blockquote>
    <div class="w-full"><image src={turtle}></image></div>
  </div>

</Slide>

<Slide>
  <h3>Different presentations</h3>
  <ul style="list-style-type: none;">
    <li>Generate image and print/plot</li>
    <li>Digital photoframe</li>
    <li>Interactive installation</li>
    <li>...</li>
  </ul>
  </Slide>

<Slide>
  <h3>Key Concepts</h3>
  <ul style="list-style-type: none;">
    <li>Artist</li>
    <li>Rules / Algorithms</li>
    <li>Randomness</li>
    <li>Repetition / Patterns</li>
    <li>Emergence</li>
  </ul>
</Slide> 

<Slide>
  <h3>Key Concepts in Action</h3>
  <P5 code={print10bis} editor autoplay />
  <Notes>
    <ul style="list-style-type: none;">
      <li>Artist</li>
      <li>Rules / Algorithms - de code - let ook dat die net iets anders is dan daarnet</li>
      <li>Randomness - elke keer ik opnieuw de code laat lopen, andere tekening</li>
      <li>Repetition / patterns- de kern van ons algoritme zijn lusjes</li>
      <li>Emergence - de tekening zelf geeft stof tot nadenken, doolhof, ...</li>
    </ul>
  </Notes>
</Slide>

<Slide>
  <h3>Some tools</h3>
  <ul style="list-style-type: none;">
    <li>Processing</li>
    <li>P5js &#128072; </li>
    <li>Sonic Pi (music)</li>
    <li>Blender</li>
    <li>Unity</li>
    <li>...</li>
  </ul>
</Slide>


<Slide url="https://p5js.org/">
</Slide>

<Slide>
  <h3>Why I <span class="text-red-400">&#10084;</span> P5js</h3>
  <ul style="list-style-type: none;" >
    <li>Online editor - nothing to install</li>
    <li>Javascript</li>
    <li>Nice and friendly documentation</li>
    <li>Gazillion tutorials online</li>
    <li>Easily extendible with other JS libraries</li>
  </ul>
</Slide>

<Slide>
  <h3>Become a generative artist 101</h3>
  <p>Some examples and quick ideas</p>
</Slide>

<Slide>
  <h3>Anatomy of a P5js sketch</h3>
  <P5 code={boilerplate} editor autoplay />
<Notes>
<p>setup() en draw()
  createCanvas()
  point() er is ook circle(), line(), rect(), ...
</p>
</Notes>
</Slide>

<Slide>
  <h3>Lines</h3>
  <P5 code={lines1} editor autoplay />
</Slide>

<Slide>
  <h3>More Interesting Lines</h3>
  <P5 code={lines2} editor autoplay />
</Slide>

<Slide>
  <h3>Squares, colors and randomness</h3>
  <P5 code={squares1} editor autoplay />
</Slide>

<Slide>
  <h3>Squares, colors and Perlin Noise</h3>
  <P5 code={squares2} editor autoplay />
</Slide>

<Slide>
  <h3>Squares, colors and Perlin Noise</h3>
  <P5 code={squares3} editor autoplay />
</Slide>

<Slide>
  <h3>Procedural landscape</h3>
  <P5 code={landscape} editor autoplay />
  <Notes>
    op lijn 25 "- frameCount / 50" toevoegen aan de y waarde
  </Notes>
</Slide>

<Slide>
  <h3>Mathematical concepts - sines and cosines</h3>
  <P5 code={sine1} editor={false} autoplay />
</Slide>

<Slide>
  <h3>Mathematical concepts - sines and cosines</h3>
  <P5 code={sine2} editor autoplay />
</Slide>

<Slide>
  <h3>Let's play</h3>
  <div class="bg-white flex flex-row justify-center align-middle"><image src={gonio}></image></div>
</Slide>

<Slide>
  <h3>Celtic Knots</h3>
  <P5 code={knots} editor autoplay />
</Slide>

<Slide>
  <h3>P5js and AI</h3>
  <P5 code={steam} editor={false} htmlPage="ml5/index.html" autoplay={false} />
</Slide>

<Slide>
  <h3>A few words on music...</h3>
  <Strudel />
</Slide>

<Slide>
  <h3>Some resources</h3>
  <ul style="list-style-type: none;">
    <li><a href="https://p5js.org/">P5js.org</a></li>
    <li><a href="https://thecodingtrain.com/">thecodingtrain.com</a></li>
    <li><a href="https://www.nerdkunst.be">nerdkunst.be</a></li>
  </ul>
</Slide>

<Slide backgroundImage={vierkanten}>
  <h3>Thank you</h3>
  <p>Go and express yourself through code &#128512;</p>
</Slide>