Title: Asking Ever Bigger Questions With Wikidata
Date: 2015-02-23 20:22
Author: max
Category: research
Slug: asking-ever-bigger-questions-with-wikidata
Status: published

This is a [Guest-Blog I wrote for Wikimedia Deutschland](http://blog.wikimedia.de/2015/02/16/asking-ever-bigger-questions-with-wikidata/): copied here:

***German summary:** [Maximilian Klein](http://en.wikipedia.org/wiki/User:Maximilianklein) benutzt Wikidata als als Datenfundus für statistische Auswertungen über das Wissen der Welt. In seinem Artikel beschreibt er, wie er in Wikidata nach Antworten auf die großen Fragen sucht.*

Asking Ever Bigger Questions with Wikidata
------------------------------------------

*Guest post by [Maximilian Klein](http://en.wikipedia.org/wiki/User:Maximilianklein)*

### [A New Era]{#A_New_Era .mw-headline}

[Simultaneous discovery](https://www.wikidata.org/wiki/Q1645643 "Q1645643") can sometimes be considered an indication for a [paradigm shift](https://www.wikidata.org/wiki/Q689971 "Q689971") in knowledge, and last month [Magnus Manske](https://www.wikidata.org/wiki/Q13520818 "Q13520818") and I seemed to have both had a very similar idea at the same time. Our ideas were to look at gender statistics in Wikidata and to slice them up by date of birth, citizenship, and langauge. ([Magnus’ blog post](http://magnusmanske.de/wordpress/?p=250){.external .text}, and [my own](http://notconfusing.com/preliminary-results-from-wigi-the-wikipedia-gender-inequality-index/){.external .text}.) At first it seems like quite elementary and naïve analysis, especially 14 years into Wikipedia, but only within the last year has this type of research become feasible. Like a baby taking its first steps, Wikidata and its tools ecosystem are maturing. That challenges us to creatively use the data in front of us.

::: {.floatright}
[![](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f5/Stages_of_Wikidata.png/400px-Stages_of_Wikidata.png){.alignright style="width:400px !important" srcset="//upload.wikimedia.org/wikipedia/commons/thumb/f/f5/Stages_of_Wikidata.png/600px-Stages_of_Wikidata.png 1.5x, //upload.wikimedia.org/wikipedia/commons/thumb/f/f5/Stages_of_Wikidata.png/800px-Stages_of_Wikidata.png 2x"}](https://commons.wikimedia.org/wiki/File:Stages_of_Wikidata.png?uselang=de "Markus Krötzsch's 5 stages of Wikdiata"){.image}
:::

Describing 5 stages of Wikidata, Markus Krötsch foresaw this analyis in his [presentation](http://korrekt.org/talks/2014/wikimania-wikidata.svg){.external .text} [at Wikimania 2014](http://new.livestream.com/wikimania/friday2014/videos/59350537){.external .text}. The stages which range from*Know* to *Understand* are: *Read*, *Browse*, *Query*, *Display*, and *Analyse* (see image). Most likey you may have read Wikidata, and perhaps even have [browsed with Reasonator](http://tools.wmflabs.org/reasonator/){.external .text}, [queried with autolist](http://tools.wmflabs.org/autolist/autolist1.html?){.external .text}, or [displayed with histropedia](http://www.histropedia.com/){.external .text}. I care to focus on *analyse* – the most understand-y of the stages. In fact the example given for *analyse* was [my first exploration of gender and language](http://notconfusing.com/sex-ratios-in-wikidata-part-iii/){.external .text}, where I analysed the ratio of female biographies by Wikipedia Language: English and German are around 15% and Japanese, Chinese and Korean are each closer to 25%.

[]{#more-21349}To do biography analysis before Wikidata was much harder. To know the gender of an article you’d resort to [natural language processing](https://www.wikidata.org/wiki/Q30642 "Q30642") or hacks like counting gendered categories and guessing based on first name. Even more, the effort had to be duplicated for each language that had to be translated. Now the promise of language-free semantic data, and tools like [Wikidata Query](https://wdq.wmflabs.org/api_documentation.html){.external .text} and [Wikidata Toolkit](https://www.mediawiki.org/wiki/Wikidata_Toolkit "mw:Wikidata Toolkit"){.extiw} are here. The process is easier because it is more database-like; *select*, *group by*,*apply*, and *combine*.

With this new simplicity, let’s review what we have imagined so far. Here’s a non-exhaustive introduction to the state of creative question-asking so far:

-   What’s [the word FOR every langauge IN every language?](http://notconfusing.com/a-word-for-every-lanaguage-in-every-language/){.external .text}
-   Which professions have the widest gender distibutions? (Asked on wiki-research mailing list: not yet anwered.)
-   What’s the connection between hospitals per population and the incidence of tuberculosis cases in cities in England from 2000-2010 ([Example from “Wikidata for Research” proposal.](https://www.wikidata.org/wiki/Wikidata:WikiProject_Wikidata_for_research "Wikidata:WikiProject Wikidata for research"))

### [Pushing Ourselves to Think Even Bigger]{#Pushing_Ourselves_to_Think_Even_Bigger .mw-headline}

Can we think even bigger if we use more of the available data? Thinking about the fact that every [*claim*](https://www.wikidata.org/wiki/Wikidata:Glossary#Claims_and_statements "Wikidata:Glossary") may have an attached [*reference*](https://www.wikidata.org/wiki/Wikidata:Glossary#Reference "Wikidata:Glossary"), Markus Krötzsch always wants to know, for a given set of claims what references must be believed in order to believe the set of claims? With that notion we could look at all the claims associated with all the items of a given language, and thus the required belief system of that langauge. At this point we could ask what are the differences in the belief systems of any two langauges?

::: {.floatleft}
[![](https://upload.wikimedia.org/wikipedia/commons/thumb/1/1a/Wikidata-wikiproject-ontology.png/200px-Wikidata-wikiproject-ontology.png){.alignleft style="width:200px !important" srcset="//upload.wikimedia.org/wikipedia/commons/thumb/1/1a/Wikidata-wikiproject-ontology.png/300px-Wikidata-wikiproject-ontology.png 1.5x, //upload.wikimedia.org/wikipedia/commons/thumb/1/1a/Wikidata-wikiproject-ontology.png/400px-Wikidata-wikiproject-ontology.png 2x"}](https://commons.wikimedia.org/wiki/File:Wikidata-wikiproject-ontology.png?uselang=de "What are the fundamental principles of all of Wikidata?"){.image}
:::

Another way we could test the fundamental principles of knowledge and culture is to consider the chains made by the [subclass of](https://www.wikidata.org/wiki/Property:P279 "Property:P279"), [instance of](https://www.wikidata.org/wiki/Property:P31 "Property:P31"), or [cause of](https://www.wikidata.org/wiki/Help:Modeling_causes "Help:Modeling causes") properties. Every language is present at different links of each chain. So we can look at the differences in ways in which languages organize a hierarchy of concepts – or if they think it’s a hierarchy at all.

Much fun for logicians and epistemologists. But we can also ask more socially important questions, questions about how language and society relate. What biases do we have that we aren’t even aware of? The method, for which I’ve [proposed a PhD](http://notconfusing.com/should-i-do-my-phd-in-the-open/#research){.external .text}, could be conducted as follows. We’re aware of sexism in our societies, and as you’ve seen we’ve started to build a statistical profile of how it manifests in Wikidata. Likewise we’re cognizant of racism and homophobia. We might next look at rates people appear in Wikidata by race and desire. Let’s assume we could train a model to say that these kinds of distributions are types of social biases. Next we could search every property in Wikidata to see if it indicated social bias. If successful we may find overlooked stigmas and phobias in society.

I claim that our theoretical question-answering ability has paradigmatically shifted with the growing up of Wikidata. Soon enough you won’t even need to be a sophisticated programmer to whisper your questions into the system. So next time your reading, browsing, querying or displaying Wikidata, challenge yourself to think about how to analyse it too.
