Title: Programming Archimedes Spirals, Polar Pong and 77 million paintings for Lights with Pixelslinger
Date: 2020-01-07 02:40
Author: max
Category: hacking
Slug: soak-lighting-2019
Status: published

## Intro
A project that I have been embarking on has been lighting art for the SOAK Burning Man regional. Here are a few pieces/programmes that I made last year of which I'm particularly proud. Of course this code is just one layer in a maze of engineering for which I have to thank [@austinfromboston](https://github.com/austinfromboston/) and [@mrstev](https://github.com/mrstev) for underpinning with their creative and dependable hardware.

## Archimedes

<iframe width="560" height="315" src="https://www.youtube.com/embed/74rhC_VQKjA" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<iframe width="560" height="315" src="https://www.youtube.com/embed/74rhC_VQKjA" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

- our target was polar
- solving this (math overflow embed) was a nice warm up in how to do the polar -> cartesian programming
- interlacing spirals
- the most interesting parameter ends up beign alpha, as you can see moving through that makes great effects.

## Pong
<iframe width="560" height="315" src="https://www.youtube.com/embed/KUEcyEN7vwE" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
- my friend harry had challenged us to make something more interactive, which is when i realized we have midi input, we could easily make a game
- saving and processing state was the main challenge (creating a very small physics similulator) but its possible in pixelslinger
- 

## 77 million paintings
<iframe width="560" height="315" src="https://www.youtube.com/embed/N5rikYAkk8E" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

- wanted to make something ambient and unrepeating. 
- clearly this is a borrow/steal from Brian Eno's project. I actually wanted to borrow the source code, but it's not available so I reimplemnted it how I thought it ought to go.

## VJing midi effects
<iframe width="560" height="315" src="https://www.youtube.com/embed/dnFJMOt1DsA" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

- we had all those midi buttons so I wanted to make some effects that you could tap out.
- the ones new for this year (And for the polar system) where the
    -  circular sweep from left nad  right
    - inward and outward concenrtic rings
- put together with the switching and parametrization of the underlying patterns there's an artform waiting to be refined for this machine.
