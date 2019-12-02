Title: A word FOR every Lanaguage IN every Language
Date: 2013-05-22 08:20
Author: max
Category: research
Slug: a-word-for-every-lanaguage-in-every-language
Status: published

Have you ever wondered what the word FOR every language was IN every language?  
Data mining Wikidata could give us the answer. Using a [new file](https://dl.dropboxusercontent.com/u/172199972/wikipedias.txt) released by Denny Vrandecic containing the Wikidata Item for each Wikidata Language I was able to create a full matrix of all the combinations.

Let L be the set of all Wikipedias. For every language X and language Y in L, does X have a [label](http://www.wikidata.org/wiki/Help:Label) for Y? Create a matrix of all the possibilities, and if X has a label Y let's colour that part of the matrix magenta, if not let's colour it cyan. Therefore you get a heatmap displaying whether the language on the X axis has a page for the language on the Y axis.

[![]({static}/images/uploads/2013/05/LanguagesByLanguages.png "LanguagesByLanguages"){.size-large .wp-image-245 style="width:1024px !important"}]({static}/images/uploads/2013/05/LanguagesByLanguages.png) A heatmap displaying whether the language on the X axis has a page for the language on the Y axis.

 

What interesting things do we find here? Well, most notably is the prominent diagonal magenta line. That's reassuring. The main diagonal of this matrix represents whether each language has a Wikidata label about itself - and it almost always does. The vertical lines show us which languages have good coverage of other languages. And the horizontal lines show us which languages have good coverage by other languages.

This should serve as a reminder that Wikidata is going to be outrageously powerful research tool.

Can you see any other patterns emerging? (The [UTF-8 CSV Matrix](https://github.com/notconfusing/wikidataLanguageMatrix/blob/master/augmentedLanguageCodes.csv), and [sourcecode.](https://github.com/notconfusing/wikidataLanguageMatrix))

Notconfusingly yours.

 
