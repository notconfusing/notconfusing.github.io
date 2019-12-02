Title: Which Index Is WIGI Most Closely Related To?
Date: 2015-02-16 01:31
Author: max
Category: research
Slug: which-index-is-wigi-most-closely-related-to
Status: published

In my lastest paper "Gender Gap Through Time and Space: A Journey Through Wikipedia Biographies and the 'WIGI' Index" ([blog post](http://notconfusing.com/preliminary-results-from-wigi-the-wikipedia-gender-inequality-index/ "Preliminary Results From WIGI, The Wikipedia Gender Inequality Index") and on [arxiv.org](http://arxiv.org/abs/1502.03086)), my co-author Piotr Konieczny and I proposed a gender index. *WIGI,* the Wikipedia Gender Inequality Index, is composed of many indicators, but one in particular, the "nation-WIGI", was designed to be comparable with other well-known indices. The nation-WIGI ranks each nation by the ratio of female biography articles who are  citizens of that nation.  Designed in this way it is possible to *correlate* WIGI to other indexes. And potentially, we thought, given enough indexes and with high enough correlations, we could get a sense for what WIGI is measuring in terms of other indices.

Due to word-count limits, we were unable to submit this research question with the rest of the paper, so it is included here. Formally we formulated is thus:

### **RQ4: Of the other Gender Indices which divide also by nation which index is Wikipedia most closely related to?**

First let's recap the four other nation divided indices we are inspecting (see [section 3 of our paper](http://arxiv.org/abs/1502.03086) for more detail).

-   **GDI**
    -   The UNDP's Gender-related Development Index (GDI) introduced only in 1995.
    -   A gender-focused extensions of the Human Development Index. GDI’s primary focus lies in gender-gaps in life expectancy, education, and incomes.

-   **GEI**
    -   The Gender Equity Index (GEI) introduced by Social Watch in 2005.
    -   Developed to measure all situations that are unfavourable to women, it ranks countries on three dimensions: education, economic participation and empowerment.

-   **GGGI**
    -   The Global Gender Gap Index (GGGI) developed by the World Economic Forum in 2006.
    -   Intended to allow comparative comparison of gender gap across different countries and years, it focuses on four areas:  economic participation and opportunity, educational attainment, political empowerment and health and survival statistic.

-   **SIGI**

    -   The Social Institutions and Gender Index (SIGI) of the OECD Development Centre from 2007.
    -   A composite indicator of gender equality that solely focuses on social institutions (norms, values and attitudes), as well as on the four dimensions of family code, physical integrity, ownership rights and civil liberties.

    Comparison Data:
    ----------------

    With each of the above four foreign indices we have a *ranking* associating a *nation* (sometimes referred to as an *economy*) and an ordinal position. We would like to understand how close two indices are, for which we use the Spearman rank correlation coefficient. Two other technical points to be addressed are that we must use the intersection of  nations covered by each index to avoid missing data problems. And lastly, we compute a *calibration step* to find the start decade of Wikidata-data that maximises the correlation in question.

    The full s[ource code of this calculation is available on github](http://nbviewer.ipython.org/github/notconfusing/WIGI/blob/master/World%20Economic%20Forum%20Comparison.ipynb).  Also as an aside, I have another blog post on an [functional-programming solution to joining many dataframes at once](http://notconfusing.com/joining-many-dataframes-at-once-in-pandas-n-ary-join/ "Joining many DataFrames at once in Pandas: “n-ary Join”"), that was useful in computing these results.

    Finally we produced a comparison table of indices,  their correlation, the correlation significance, and the maximizing start decade.  We present it ordered by correlation:

    
    <table width="624" cellspacing="0" cellpadding="7">
    
    
    <colgroup>
    
    
    <col width="141">
    
    
    </col>
    
    
    <col width="142">
    
    
    </col>
    
    
    <col width="142">
    
    
    </col>
    
    
    <col width="141">
    
    
    </col>
    
    
    </colgroup>
    
    
    <tbody>
    
    
    <tr>
    
    
    <td colspan="4" valign="top" style="width:608px !important">
    
    National-WIGI compared to Alternative Indexes
