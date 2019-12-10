Title: 3 Ways To Access Wikidata Data Until It Can Be Done Properly
Date: 2016-05-02 02:40
Author: max
Category: hacking
Slug: 3-ways-to-access-wikidata-data-early
Status: published

Note: This post is quite old. In fact Wikidata can now be accessed "properly" via the [Wikidata Query Service (WDQS).](https://query.wikidata.org/) However the techniques outlined below still have their advantages.

The inaugural [Wiki Research Hackathon](https://meta.wikimedia.org/wiki/Research:Labs2/Hackathons/November_9th,_2013) went very well, and I'm affirmed that I feel best when I'm conducting Wiki Research. I was asked to give one of the tech talks of the day about accessing Wikidata data programmatically. Here is an outline of the talk

### Purpose:

We'll be viewing Wikidata as file in its own right for research, not as it's canonical use case of being used in various Wikipedias.

### Native format:

Wikidata is a mostly standard Mediawiki instance except that pages don't store "Wikitext", they store JSON blobs. (If you want to understand more about this abstraction, see then [ContentHandler](http://www.mediawiki.org/wiki/Manual:ContentHandler)).

### Structure of a Wikidata Item:

Main entry point of any Wikidata item is a JSON dictionary, that has this form:

    {“labels”: by-language dictionary

    “descriptions”: by-language dictionary

    “aliases”: by-language dictionary

    “claims”: list of property and values

    “sitelinks”: by-language dictionary}

 

### 3 Ways To Access Wikidata:

Whether your more comfortable in object-oriented python, parsing large text files, or munging linked data, there is something for you.

-   Live, from the API, using [pywikibot](http://www.mediawiki.org/wiki/Manual:Pywikibot/Wikidata)
    -   Read / write
-   Offline, dumps, using Wikidata Toolkit (wdtk)
    -   Newer, shinier, performant Java
        -   <https://www.mediawiki.org/wiki/Wikidata_Toolkit>
    -   Deprecated, slower, unmaintained python "Wikidata Analyzer"
        -   <https://github.com/mkroetzsch/wda>
    -   Read only
-   As linked data, entities, via content negotiation
    -   Read only

### Using Pywikibot:

With pywikibot you get almost full support of the API.  
New classes in the “core” branch  
class WikibasePage(Page):  
class ItemPage(WikibasePage):  
class PropertyPage(WikibasePage):  
class Claim(PropertyPage):  
Using Pywikibot  
Classic pywikibot pagegenerators work.  
\#make a generator for all the pages with a property  
en_wikipedia = pywikibot.Site('en', 'wikipedia')  
wikidata = en_wikipedia.data_repository()  
property_page = pywikibot.ItemPage(wikidata, 'Property:P21')  
pages_with_property = property_page.getReferences()

#### Pywikibot example:

I've been harvesting Infobox Book across many languages and writing the corresponding properties to Wikidata <https://github.com/notconfusing/harvest_infobox_book>.

### Using wda

[Update: WDA is deprecated and replaced by Wikidata Toolkit, which I explain how to use with code examples [in this blog post.](http://notconfusing.com/sex-ratios-in-wikidata-part-iii/ "Sex Ratios in Wikidata Part III")]{style="font-size: 14pt;"}

WDA, WikiData Analytics, downloads the official dump and analyzes it offline. Cleverly it uses nightly incremental dumps after about a 10GB first download. It's also written in python, mainly by Markus Kroetzsch.After downloading there is a parser that writes a file called kb.txt. kb.txt stores plaintext triples, one per line giving you something like this.

    Q21 link {trwiki:İngiltere} .
    Q21 link {hewiki:אנגליה} .
    Q21 alias {en:ENG} .
    Q21 alias {min:Inggirih} .
    Q21 alias {sgs:England} .
    Q21 P31 Q1763527 .
    Q21 P47 Q22 .
    Q21 P47 Q25 .
    Q21 P41 {Flag of England.svg} .

    I used wda to in my analysis of the most unique Wikipedias according to Wikidata.

### Content Negotiation:

You can also access Wikidata as linked data. The build path is:

    https://wikidata.org/entity/<QID>.<format>

where your choices of format are

    nt
    rdf
    ttl

Content Negotiaton Example

    https://www.wikidata.org/wiki/Special:EntityData/Q42046.ttl @prefix entity: <http://www.wikidata.org/entity/> . @prefix wikibase: <http://www.wikidata.org/ontology#> . @prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> . @prefix skos: <http://www.w3.org/2004/02/skos/core#> . @prefix schema: <http://schema.org/> . @prefix data: <http://www.wikidata.org/wiki/Special:EntityData/> . @prefix cc: <http://creativecommons.org/ns#> . @prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

    entity:Q42046
     a wikibase:Item ;
     rdfs:label "鬣狗科"@zh, "Hienowate"@pl, "Hiena"@eu, "Hyaenidae"@es, "Hiëna"@af, "Dubuk"@ms, "Hiénafélék"@hu, "Fisi"@sw, "Hüäänlased"@et, "হায়েনা"@bn, "Hiena"@sq, "Hyaenidae"@br, "Ύαινα"@el

### Conclusion

So until [Phase III](http://en.wikipedia.org/wiki/Wikidata#Phase_3) there are still some usable options to explore Wikidata for research purposes. However we can still dream of future robust query system. In that dream I like to think of a query system capable of answering "does there exists is a sequence of properties that connects these two Wikidata items?"
