Title: Programming Archimedes Spirals, Polar Pong and 77 million paintings for Lights with Pixelslinger
Date: 2020-01-07 02:40
Author: max
Category: hacking
Slug: soak-lighting-2019
Status: published

## Intro
A project that I have been tinkering with for the last few years has been lighting art for the SOAK Burning Man regional. Here are a few pieces/programmes that I made last year of which I'm particularly proud. Of course this code is just one layer in a maze of engineering for which I have to thank [@austinfromboston](https://github.com/austinfromboston/) and [@mrstev](https://github.com/mrstev) for underpinning with their creative and dependable hardware.

## Archimedes
<iframe width="560" height="315" src="https://www.youtube.com/embed/BzDiT-ngDAk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<iframe width="560" height="315" src="https://www.youtube.com/embed/74rhC_VQKjA" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

The very first concept I thought about when I saw the "fan" shape hardware that my collaborators had made, was that the display was polar — and we should design for it using polar equations. Then my obession with spirals started. I love that spirals have the equation r=θ in polar, which relates the two dimension variables, like y=x in cartesian. Spirals are lines. Or are lines spirals?

Solving how to program the spiral was simple, but figuring out how to rotate the spiral took some pencil and paper headscratching which I explain at [math.stackexchange](https://math.stackexchange.com/questions/154743/how-to-rotate-a-polar-equation/3150953#3150953).

This pattern I call Archimedes with it's overlaying spirals an homage to the grecian populariser. I found that with multiple spirals of the family r=αθ sweeping between α in the range \[-10, 10\] can makes a cool burst pattern.

- Code: [https://github.com/austinfromboston/pixelslinger/blob/soak_2019/opc/pattern-archimedes.go](https://github.com/austinfromboston/pixelslinger/blob/soak_2019/opc/pattern-archimedes.go)
- Ported to shadertoy so you can play with it live: (thanks @austinfromboston) [https://www.shadertoy.com/view/3dGSDt](https://www.shadertoy.com/view/3dGSDt)

## Polar VJing midi effects
<iframe width="560" height="315" src="https://www.youtube.com/embed/dnFJMOt1DsA" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

After becoming proficient with programming polar equations in the cartesian pixelslinger, I wanted to create some circular and radial VJing effects that could be played with on the midi pad.
The ones new for this year for the polar system were the:

- circular sweep from left and right
- inward and outward concentric rings

which can be seen shown off at around the 3 minute mark. Put together with the switching and parametrization of the underlying patterns there's an artform waiting to be refined for VJing this machine.

- Code: [https://github.com/austinfromboston/pixelslinger/blob/soak_2019/opc/effect-fader.go](https://github.com/austinfromboston/pixelslinger/blob/soak_2019/opc/effect-fader.go)


## 77 million paintings
<iframe width="560" height="315" src="https://www.youtube.com/embed/N5rikYAkk8E" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

As well button-mashing I wanted something that was entertaining without it needing any VJing input. I wanted to be able to walk away from the lighting and people could still drink tea by it. I decide it shouldn't be frenetic and it should have no clear repeating patterns. I decided to borrow/steal from Brian Eno's 77 million painting artwork which I was infatuated with. Quickly, the idea is to have procedurally generated paintings which are combinatoric layerings of base-elements. In the original there are 77million combinations. I made 78 layers and 4 are being displayed at a time so just 78 choose 4 paintings for me. The transparency of each layer is being modulated on staggered sine-waves. I actually wanted to borrow the source code of the original, but it's not available so I reimplemented it how I thought it ought to go.

- Code: [https://github.com/austinfromboston/pixelslinger/blob/soak_2019/opc/pattern-77million.go](https://github.com/austinfromboston/pixelslinger/blob/soak_2019/opc/pattern-77million.go)

## Polar Pong
<iframe width="560" height="315" src="https://www.youtube.com/embed/KUEcyEN7vwE" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

After seeing our first attempt at lighting last year, my friend Harry challenged us to make something more interactive, like a game, "like pong" he said. I couldn't say no to the challenge once I realized that our current technology supported that just as it was. The hard part was storing and passing around the game state (and creating a very small physics engine) but it's all possible in pixelslinger. I wish I had some video of it being played live, but alas I never want to carry my phone around at these events.

- Code: [https://github.com/austinfromboston/pixelslinger/blob/soak_2019/opc/pattern-pong.go](https://github.com/austinfromboston/pixelslinger/blob/soak_2019/opc/pattern-pong.go)
