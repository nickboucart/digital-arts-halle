<script lang="ts">
	import Slide from './slide.svelte'
	import Notes from './notes.svelte'
	import P5 from '$lib/components/P5.svelte'
  import CodeBlock from '$lib/deck/code.svelte'

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

let print10bislijn1 = `const size = 25;
const cutoff = 0.5;

function setup() {
  createCanvas(500, 400);
  background("#111111");
  noLoop();
}

function draw() {
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
let print10bislijn2 = `const size = 10;
const cutoff = 0.5;

function setup() {
  createCanvas(500, 400);
  background("#111111");
  noLoop();
}

function draw() {
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

let print10biskleur1 = `const size = 15;
const cutoff = 0.5;

function setup() {
  createCanvas(500, 400);
  background("green");
  noLoop();
}

function draw() {
  stroke("yellow");
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

let print10biskleur2 = `const size = 15;
const cutoff = 0.5;

function setup() {
  createCanvas(500, 400);
  background("teal");
  noLoop();
}

function draw() {
  stroke("cyan");
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


let print10bisrand1 = `const size = 15;
const cutoff = 0.1;

function setup() {
  createCanvas(500, 400);
  background("teal");
  noLoop();
}

function draw() {
  stroke("cyan");
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

let print10bisrand2 = `const size = 15;
const cutoff = 0.8;

function setup() {
  createCanvas(500, 400);
  background("teal");
  noLoop();
}

function draw() {
  stroke("cyan");
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

let landscape2 = `let zoom = 0.01;

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
}

function draw() {
  background(220);
  for (let x = 0; x < width; x++) {
    for (let y = 0; y < height; y++) {
      // noise geeft getal tussen 0 en 1, dat we omzetten naar een grijswaarde tussen 0 en 255
      let kleur = noise(x * zoom, y * zoom - frameCount / 50);
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

let fireworks = `function createSingleArrowRandomly() {
  return new VuurwerkPijl(random(["red", "grape", "pink", "violet", "indigo", "blue", "cyan", "teal", "green", "lime", "yellow", "orange"]));
}

class FireWorkShow {
  constructor(maxNbrOfArrows) {
    this.maxNbrOfArrows = maxNbrOfArrows;
    this.currentNbrOfArrows = 1;
    this.arrows = [createSingleArrowRandomly()];
  }

  update() {
    for (var arrow of this.arrows) {
      arrow.update();
    }
    this.arrows = this.arrows.filter((a) => {
      return !a.hasFaded();
    });
    if (this.arrows.length === 0) {
      this.currentNbrOfArrows = 2*this.currentNbrOfArrows;
      if (this.currentNbrOfArrows > this.maxNbrOfArrows) {
        this.currentNbrOfArrows = 1;
      }
      for (var i = 0; i < this.currentNbrOfArrows; i++) {
        this.arrows.push(createSingleArrowRandomly());
      }
    }
  }

  draw() {
    for (var arrow of this.arrows) {
      arrow.draw();
    }
  }
}

class Rocket {
  constructor(myColor) {
    this.color = myColor;
    this.pos = createVector(width/2, height);
    this.velocity = createVector(random(-3, 3), random(-5, -10));
    this.acceleration = createVector(0, 0.1)
  }
  
  update() {
    this.velocity.add(this.acceleration);
    this.pos = this.pos.add(this.velocity);
    
  }
  
  draw() {
    stroke(colors[this.color][8]);
    fill(colors[this.color][8]);
    circle(this.pos.x, this.pos.y, 5);
  }
  
  hasExploded() {
    // de racket ontploft op haar hoogste punt, op dat moment is haar vertikale snelheid 0, of net positief
    return this.velocity.y >= 0;
  }
}

class VuurwerkPijl {
  constructor(myColor) {
    this.x = 0;
    this.y = 0;
    this.rocket = new Rocket(myColor);
    this.hasExploded = false;
    this.particles = [];
    this.color = myColor;
    }

  hasFaded() {
    // een pijl is volledig uitgebrand als de racket ontploft is en alle particles opgebrand
    return (this.hasExploded && this.particles.length === 0);
  }

  draw() {
    if (!this.rocket.hasExploded()) {
      //de racket is nog niet ontploft. die moet gewoon verder vliegen
      this.rocket.draw();
      return;
    }
    for (var p of this.particles) {
      p.draw();
    }
  }

  rocketJustExplodedAddParticles() {
    // de racket is pas ontploft, we moeten particles aanmaken
    this.hasExploded = true; //beetje extra boekhouding
    let phase = random(0, 1);
    for (let i = 0; i < 20; i++) {
      this.particles.push(
          new Particle(this.rocket.pos.x, this.rocket.pos.y, 2, phase * PI + (i * TWO_PI) / 20, this.color)
      );
    }
  }
  
  didRocketJustExplode() {
    return (this.rocket.hasExploded() && this.particles.length === 0);
  }

  update() {
    if (!this.rocket.hasExploded()) {
      //de racket is nog niet ontploft. die moet gewoon verder vliegen
      this.rocket.update();
      return;
    }
    if (this.didRocketJustExplode()) {
      //racket is juist ontploft, we maken de deeltjes
      this.rocketJustExplodedAddParticles()
    }
    //en we updaten de deeltjes en verwijderen eventueel opgebrande deeltjes.
    for (var p of this.particles) {
          p.update();
    }
    //remove all invisible/burned particles
    this.particles = this.particles.filter((p) => {
      return !p.invisible;
    });
    
    
  }
}

class Particle {
  //radius is de afstand van het middelpunt van de ontploffing, angle slaat op de hoek waaronder het deeltje wegvliegt.
  constructor(x, y, radius, angle, myColor) {
    this.x = x;
    this.y = y;
    this.radius = radius;
    this.angle = angle;
    this.color = myColor;
    this.size = 2;
    this.invisible = false;
  }

  update() {
    this.radius += 1;
    this.size += 0.025;
    if (this.radius > 250) {
      this.invisible = true;
    }
  }

  draw() {
    if (this.invisible) return;
    push();
    var colorIndex = 9-floor(map(this.radius, 1, 250, 0, 9, true));
    stroke(colors[this.color][colorIndex]);
        fill(colors[this.color][colorIndex]);
    translate(this.x, this.y);
    circle(this.radius * sin(this.angle), this.radius * cos(this.angle), this.size);
    pop();
  }
}

let fireworkShow;
let rocket;
let colors;

function preload() {
  colors = loadJSON('open-colors.json');
}

function setup() {
  createCanvas(600, 600);
  fireworkShow = new FireWorkShow(129);
  
}

function draw() {
  background(50);
  fireworkShow.update();
  fireworkShow.draw();
}
`

let steam = `let video;
let pose;
let bodyPose;

function preload() {
  // Load the bodyPose model
  bodyPose = ml5.bodyPose("MoveNet", {modelType: "SINGLEPOSE_LIGHTNING", modelUrl: "/movenet/model.json"});
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
</script>


<Slide backgroundImage={vierkanten}>
	<!-- todo: background image van de site en veel betere styling van tekst -->
	<h1 class="text-black">NerdKunst</h1>
	<p>Omdat wetenschap en technologie soms ook gewoon leuk en mooi kunnen zijn.</p>
  <p class="text-right text-xl">Nick Boucart - nerdkunst.be</p>
</Slide>

<Slide>
  <p>Maak in een paar minuutjes kennis met de wondere wereld van <strong>generatieve kunst</strong></p>
</Slide>

<Slide>
  <p>Generatieve kunst is kunst die wordt gecreëerd met behulp van een <span class="italic">systeem</span> (een algoritme, een computerprogramma of regels). </p>
</Slide>

<Slide>
  <p> Vaak speelt willekeur (randomness) een rol in dit proces, waardoor elk gegenereerd kunstwerk uniek is en onvoorspelbare variaties kan vertonen. </p>
</Slide>

<Slide autoslide={4000}>
  <h3>Een voorbeeldje gaat veel duidelijk maken &#128521;</h3>
  </Slide>

  <Slide autoslide={2000}>
    <p class="">Stel, je tekent je scherm vol met schuine streepjes.</p>
    <p class="fragment fade-in">Voor je een streepje tekent, gooi je een muntje op.</p>
    <p class="fragment fade-in">Bij kop teken je een schuin streepje naar links. </p>
    <p class="fragment fade-in">Bij munt een / </p>
    <p class="fragment fade-in">Hoe zou je tekening eruit zien?</p>
  </Slide>
 
<Slide autoslide={20*1000}>
  <P5 code={print10} editor={false} autoplay={true} /> 
</Slide> 

<Slide>
  <h3>Dit is een bekende one-liner uit de jaren 1980 op de Commodore 64</h3>
 <CodeBlock code={"10 PRINT CHR$(205.5+RND(1)); : GOTO 10"}/>

</Slide> 

<Slide>
  <h3>Elke keer je dit programmaatje laat lopen, krijg je een andere, unieke tekening, kijk zelf!</h3>
</Slide>

<Slide autoslide={500}>
  <p class="hidden">lege slide omdat anders transitie raar doet.</p>
</Slide>

<Slide transition={"none"}>
  <P5 code={print10bis} editor={false} autoplay />
</Slide>

<Slide transition={"none"} >
  <P5 code={print10bis} editor={false} autoplay />
</Slide>

<Slide transition={"none"} >
  <P5 code={print10bis} editor={false} autoplay />
</Slide>
<Slide transition={"none"}>
  <P5 code={print10bis} editor={false} autoplay />
</Slide>


<Slide>
  <h3>Fascinerend, niet? &#128521;</h3>
</Slide>

<Slide>
  <h3>Het wordt nog interessanter met wat variatie!</h3>

</Slide>
<Slide transition={"none"}>
  <h3>Grotere streepjes</h3>
  <P5 code={print10bislijn1} editor autoplay />
</Slide>
<Slide transition={"none"}>
  <h3>Kleinere streepjes</h3>
  <P5 code={print10bislijn2} editor autoplay />
</Slide>
<Slide transition={"none"}>
  <h3>Kleuren</h3>
  <P5 code={print10biskleur1} editor autoplay />
</Slide>
<Slide transition={"none"}>
  <h3>Kleuren</h3>
  <P5 code={print10biskleur2} editor autoplay />
</Slide>

<Slide transition={"none"} >
  <h3>Hoeveelheid willekeur</h3>
  <P5 code={print10bisrand1} editor autoplay />
</Slide>
<Slide transition={"none"} >
  <h3>Hoeveelheid willekeur</h3>
  <P5 code={print10bisrand2} editor autoplay />
</Slide>

<Slide>
  <h3>Nog enkele voorbeelden, de code staat er altijd naast</h3>
  </Slide>

<Slide>
  <h3>Vierkanten, kleuren en willekeur</h3>
  <P5 code={squares1} editor autoplay />
</Slide>

<Slide>
  <h4>Vierkanten, kleuren en Perlin Noise <span>(minder chaotische willekeur)</span></h4>
  <P5 code={squares3} editor autoplay />
</Slide>

<Slide>
  <h3>Een proceduraal landschap</h3>
  <P5 code={landscape} editor autoplay />

</Slide>
<Slide autoslide={30*1000}>
  <h3>Vliegen over een proceduraal landschap</h3>
  <P5 code={landscape2} editor autoplay />

</Slide>

<Slide>
  <h4>Generatieve kunst <span class="text-red-400">&#10084;</span> Wiskunde</h4>
</Slide>

<Slide autoslide={30*1000}>
  <h4>Spelen met sinus en cosinus</h4>
  <P5 code={knots} editor autoplay />
</Slide>

<Slide autoslide={60*1000}>
  <h4>Verdubbelend vuurwerk - exponentiële groei</h4>
  <P5 code={fireworks} editor autoplay />
</Slide>
<Slide>
  <h4>Het kan ook interactiever en ludieker</h4>
  <p>Met de webcam en AI</p>
</Slide>

<Slide autoslide={60*1000}>
  <h4>Stoom uit je oren! </h4>
  <P5 code={steam} editor={false} htmlPage="ml5/index.html" autoplay />
</Slide>

<Slide>
  <h3>Zelf aan de slag?</h3>
  <ul style="list-style-type: none;">
    <li><a href="https://p5js.org/">P5js.org</a></li>
    <li><a href="https://www.nerdkunst.be">nerdkunst.be</a></li>
    <li><a href="https://www.coderdojobelgium.be">coderdojobelgium.be</a></li>
  </ul>
</Slide>


<Slide backgroundImage={vierkanten}>
  <p>Ga en druk je uit via code &#128512;</p>
  <p>Nick Boucart - CoderDojo Halle - nerdkunst.be</p>
</Slide>