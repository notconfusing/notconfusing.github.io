Title: Method of Reflections: Explained and Exampled in Python
Date: 2014-06-09 06:53
Author: max
Category: hacking
Slug: method-of-reflections-explained-and-exampled-in-python
Status: published

[The introduction of post is mirrored here, but the full tutorial is [on IPython Notebook Viewer](http://nbviewer.ipython.org/github/notconfusing/wiki_econ_capability/blob/master/Method%20of%20Reflections%20Explained%20and%20Exampled.ipynb).]{style="font-size: 18pt;"}

::: {#notebook .border-box-sizing tabindex="-1"}
::: {#notebook-container .container}
::: {.cell .border-box-sizing .text_cell .rendered}
::: {.inner_cell}
::: {.text_cell_render .border-box-sizing .rendered_html}
Method of Reflections Explained and Exampled in Python
======================================================

 

[![See how the Method of Reflections evolves as a recursive process.]({static}/images/uploads/2014/06/example_evolution.png){.size-medium .wp-image-683 style="width:295px !important"}]({static}/images/uploads/2014/06/example_evolution.png) See how the Method of Reflections evolves as a recursive process.

The Method of Reflection (MOR) is a algorithm first coming out of macroeconomics, that ranks nodes in a bi-partite network. This notebook should hopefully help you implement the *method of reflection* in python. To be precise, it is the modified algorithm that is proposed by Caldarelli et al., which solves some problems with the original Hidalgo-Hausmann (HH) algorithm [doi:10.1073/pnas.0900943106](http://chidalgo.com/Papers/HidalgoHausmann_PNAS_2009_PaperAndSM.pdf). The main problem with (HH) is that all values converge to a single fixed point after sufficiently many iterations. The Caldarelli version solves this by adding a new term to the recursive equation - what they call a *biased random walker* (function *G*). [doi: 10.1371/journal.pone.0047278](http://www.plosone.org/article/info%3Adoi%2F10.1371%2Fjournal.pone.0047278) . I hadn't seen any open-source implementations of this algorithm, so I thought I'd share my naïve approach.
:::
:::
:::

Read on at <http://nbviewer.ipython.org/github/notconfusing/wiki_econ_capability/blob/master/Method%20of%20Reflections%20Explained%20and%20Exampled.ipynb>
:::
:::



 

 
