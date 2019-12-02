Title: The Topmost Cited DOIs on Wikipedia
Date: 2014-04-10 00:14
Author: max
Category: research
Slug: the-topmost-cited-dois-on-wikipedia
Status: published

You're surfing a topic of great interest to you on Wikipedia, so interesting that you actually click through to the references. You're excited to read the original material, but all of a sudden you are foiled—*you've hit a paywall!* And **\$35** to read an article is just too steep.

![Fish](https://upload.wikimedia.org/wikipedia/commons/thumb/c/cb/Xanthichthys_ringens_-_pone.0010676.g191.png/600px-Xanthichthys_ringens_-_pone.0010676.g191.png){style="width:360px !important"} This image of [Xanthichthys ringens](https://en.wikipedia.org/wiki/Xanthichthys_ringens) is sourced from an open-access scholarly article licensed for re-use. How can we make that reusability explicit when citing this source in Wikipedia articles? For further details, see this [Signpost op-ed](https://en.wikipedia.org/wiki/Wikipedia:Wikipedia_Signpost/2014-01-15/Op-ed) by Daniel Mietchen.

[The Wikipedia Open Access Signalling Project](https://en.wikipedia.org/wiki/Wikipedia:WikiProject_Open_Access/Signalling_OA-ness), which I've recently joined, sees this as a fantastic opportunity to spread the word about the [Open Access (OA) movement](https://en.wikipedia.org/wiki/en:Open_Access "w:en:Open Access"). We are still in the initial stages of understanding what OA materials are currently cited on-wiki. One of the ways OA has been cited on Wikipedia so far is through the [Template:Cite DOI](https://en.wikipedia.org/wiki/Template:Cite_doi). A Digital Object Identifier (DOI) can be thought of as ISBNs for articles - academic or otherwise - in the networked world.

The DOI becomes useful in citations because, like with any identifier, one can unmistakably and machine-readably know what is being cited. For the OA Signalling Project machine-readability is key. It will allow us to tell readers whether a cited resource is OA or free-to-read before they even click on it. By analysing the usage of DOIs on Wikipedia we can see what areas are starting to catch on to this slick method of citation.

Our method comes from processing the English Wikipedia database dumps from March 2014.  Hattip going to the wonderful [python tools](https://pypi.python.org/pypi/mediawiki-utilities/0.2.1) written by Wikimedia Foundation Analytics member [Aaron Halfaker.](https://twitter.com/halfak) Note this analysis is strictly looking for the *Cite doi* template, so it doesn't take into account DOIs that are mentioned in the *Cite journal* template.

Let's start off with a surface inquiry - what are the top most used DOIs by number of Wikipedia pages that cite them? Below are the top 10.

   DOI                                  Article Title                                                                                                Times Cited
  ------------------------------------- ------------------------------------------------------------------------------------------------------------ -------------
  10.1128/MCB.22.19.6663-6668.2002      Purified Box C/D snoRNPs Are Able To Reproduce Site-Specific 2′-O-Methylation of Target RNA In Vitro         171
  10.1093/icb/icr006                    Evolution and Ecology of Directed Aerial Descent in Arboreal Ants                                            132
  10.1093/nar/gkj002                    A novel experimental approach for systematic identification of box H/ACA snoRNAs from eukaryotes             75
  10.1128/MCB.24.13.5797-5807.2004      Human Box H/ACA Pseudouridylation Guide RNA Machinery                                                        66
  10.1088.2F0004-6256.2F141.2F5.2F170   Rotational properties of Jupiter Trojans I. Light curves of 80 objects.                                      64
  10.1093/emboj/20.11.2943              Cajal body‐specific small nuclear RNAs: a novel class of 2′‐O‐methylation and pseudouridylation guide RNAs   50
  10.1088/0004-637X/753/2/156           Parallaxes and proper motions of ultracool brown dwarfs of spectral types Y and late T.                      38
  10.1088/0067-0049/197/2/19            The first hundred brown dwarfs discovered by the wide-field infrared survey explorer.\`                      33
  10.3897/zookeys.242.3856              A new species of Schrankia Hübner, 1825 from China (Lepidoptera, Erebidae, Hypenodinae)                      28
  10.1073/pnas.242603899                Generation and initial analysis of more than 15,000 full-length human and mouse cDNA sequences               27

From an individual article point of view, we can see that Biology performs very well with many articles about molecular and cell biology being widely cited. Also in 2nd and 9th place a study of ants and moths get their due. Astronomy also seems to find success with 3 positions in the top 10.  However if one looks at the articles in which these citations occur, they appear to be mostly stub pages about RNA variations, or outlying stars. We know that each citation is not equal however because those citations on pages that receive more views will gain more exposure. We adapt our method to sum of the page views of each page on which the DOI appears.  To do this we used [Wiki View Stats](https://tools.wmflabs.org/wikiviewstats/) which is quickly becoming a valid alternative to the under-strain [stats.grok.se](http://stats.grok.se) . This top 10 *by viewership* tells a very different story.

   DOI                           Article Title                                                                                                      Views in March '14
  ------------------------------ ------------------------------------------------------------------------------------------------------------------ --------------------
  10.1038/460787a                Climate data spat intensifies                                                                                      2,767,151
  10.1038/462545a                Climatologist under pressure                                                                                       2,766,979
  10.1353/cwh.1969.0065          *Twelve Years a Slave* (review)                                                                                    1,382,286
  10.1145/1284621.1284635        Why you can't cite Wikipedia in my class                                                                           1,313,264
  10.1371/journal.pone.0028705   ‘*Nedoceratops*’: An Example of a Transitional Morphology                                                          1,216,279
  10.1126/science.1173983        Recent Warming Reverses Long-Term Arctic Cooling                                                                   704,326
  10.1038/nature06949            High-resolution carbon dioxide concentration record 650,000-800,000 years before present                           646,251
  10.1073/pnas.0805721105        Proxy-based reconstructions of hemispheric and global surface temperature variations over the past two millennia   646,251
  10.1080/10807030802387556       A Comparative Analysis of Accident Risks in Fossil, Hydro, and Nuclear Energy Chains                              624,108
  10.1098/rsbm.1955.0005          Albert Einstein. 1879-1955                                                                                        544,353

Firstly some of these citations are receiving a large audience, the topmost gets 2.75 million views in March 2014. True, the article is not being read directly, but some of its content is being transmitted with each read of the page. Also the over all feeling of these citations is different. Somehow they are less rigorously academic, and on more controversial topics. Clearly climate change features heavily, which is both a testament to the public wanting to read about climate change topics, and also the desire of Wikipedians to cite those pages thoroughly. This new perspective is essentially a new [altmetric](https://en.wikipedia.org/wiki/Altmetrics).

While we are investigating individual DOIs, we can use the fact that a DOI has a prefix-suffix composition. The prefix indicates the "registrant" (usually a publisher),  and the suffix what item it is of that publisher. What are the most used DOI prefixes? Below are the top 10.

   Prefix   Name                                                         DOIs in Use
  --------- ------------------------------------------------------------ -------------
  10.1016   Elsevier                                                     3398
  10.1038   Nature Publishing Group                                      1879
  10.1007   Springer-Verlag                                              1793
  10.1098   The Royal Society                                            1716
  10.1111   Wiley Blackwell (Blackwell Publishing)                       1350
  10.1093   Oxford University Press                                      1203
  10.1002   Wiley Blackwell (John Wiley & Sons)                          960
  10.1021   American Chemical Society                                    873
  10.1126   American Association for the Advancement of Science (AAAS)   821
  10.1080   Informa UK (Taylor & Francis)                                704

With Elsevier dominating the top spot, it shows there is still a lot of growth for OA citations on Wikipedia. Also there are other registrants here which are do not support OA policies. If you know more about the OA-ness of each of these top 10, we would like to hear.  Anecdotally, If we take information about Journal citations that do not use DOIs but rather use [Template:Cite Journal](http://en.wikipedia.org/wiki/Template:Cite_journal) then we find that this isn't an unusual distribution, [as the top cited Journals from fuzzy of Template:Cite Journal](https://en.wikipedia.org/wiki/Wikipedia:WikiProject_Academic_Journals/Journals_cited_by_Wikipedia/Popular1) have a lot of overlap.

Some of this analysis could already be performed by "Cite-o-meter", an existing service answering queries at <http://toolserver.org/~dartar/cite-o-meter/> developed in 2011. However cite-o-meter has not seen development in a few years, yet it acutally allows us to think bigger about theses statistics. It would be a worthwhile undertaking to merge or add to cite-o-meter the altmetric of *citation strength by Wikipedia pageviews.* In fact such a service could include publisher strength by Wikipedia pageviews, as well as Researcher strength by using DOI associated [OrcIDs](http://orcid.org/).

Lastly we can flip our previous question, trying to determine which pages use the most DOIs?

  Page Name                             Times Cited
  ------------------------------------- -------------
  Induced stem cells                    189
  List of Ig Nobel Prize winners        91
  Asymmetric hydrogenation              86
  Spinal muscular atrophy               84
  Crystallographic defects in diamond   80
  Fluorine                              78
  Fullerene chemistry                   54
  Choosing Wisely                       50
  Woolly mammoth                        47
  Health effects of tobacco             43

The list is as you might expect is power-law distributed. In fact 60.6% of pages that have any DOI citation, have only one. But among these top citing pages we see a large amount of science articles, some of which are quite obscure and recondite. However one article that is promising to the OA signalling cause is "Health effects of tobacco", because it appears on the [WikiProject:Medicine top-importance list](https://en.wikipedia.org/wiki/Wikipedia:MED#Goals). And one of the ways that the OA signalling project plans to prove its worth is by focusing foremost on those medical articles that the web reads for truly important information.

Our next tasks is to start writing a bot that will be able to automatically determine the OA-ness of a citation using some new APIs that have been released by publishers. At that point we will be able to know what percentage of citations on Wikipedia can actually be read by general public.

To learn more about the OA signalling project you can follow our progress on [Github](https://github.com/Daniel-Mietchen/OA-signalling). For code to this anlysis, check out the [ipython notebooks](https://github.com/Daniel-Mietchen/OA-signalling/tree/master/cite_doi_analysis).
