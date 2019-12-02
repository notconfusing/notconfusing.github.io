Title: Wiki-Class Set-up Guide and Exploration
Date: 2014-07-06 21:58
Author: max
Category: hacking
Slug: wiki-class-set-up-guide-and-exploration
Status: published

[[Best viewed with IPython Notebook Viewer](http://nbviewer.ipython.org/github/notconfusing/Wiki-Class/blob/master/Wiki-Class%20Set-up%20Guide%20and%20Exploration.ipynb)]{style="font-size: 18pt;"}

------------------------------------------------------------------------

 

::: {.text_cell_render .border-box-sizing .rendered_html}
Wiki-Class Set-up Guide and Exploration
=======================================

[Wiki-Class](http://pythonhosted.org/wikiclass/) is python package that can determine the *quality* of a Wikipedia page, using machine learning. It is the open-sourcing of the [Random Forest](https://www.wikidata.org/wiki/Q245748#sitelinks-wikipedia) algorithm used by [SuggestBot](https://en.wikipedia.org/wiki/User:SuggestBot). SuggestBot is an opt-in recommender to Wikipedia editors, offering pages that need work which look like pages they've worked on before. Similarly, with this package, you get a function that accepts a string of [wikitext](https://en.wikipedia.org/wiki/Wikipedia:Wikitext), and returns a [Wikipedia Class ('Stub', 'C-Class', 'Featured Article', etc.)](https://en.wikipedia.org/wiki/Wikipedia:Quality_scale#Grades). Wiki-class is currently in `alpha` according to its packager and developer [\[\@halfak\]]{.citation}(https://twitter.com/halfak), and although I had to make a few patches to get some examples to work, it's ready to start classifying your wikitext.

Overview
========

1.  Setting it up on Ubuntu.
2.  Testing the batteries-included model.
3.  Using the output by introducing a closeness measure.
4.  Testing making our own model.

Setup
-----

At first you may be frustrated to learn that Wiki-Class is Python 3 only. You'll not be able to mix it with pywikibot, which is Python 2.7 only, and that can also mean upgrading some of your other tools. However just try to recall these update gripes next time you encounter a UnicodeError in Python 2.x; and then be thankful to Halfak for making us give Python 3 a try. I outline getting the environment running in Ubuntu 14.04 here.

Firstly, if you want to use the Ipython notebook with python3 you can do so with `apt-get`. And while we're at it, for convenince we'll also install another version of pip for Python 3.
:::

::: {.cell .border-box-sizing .code_cell .vbox}
::: {.input .hbox}
::: {.prompt .input_prompt}
In \[95\]:
:::

::: {.input_area .box-flex1}
::: {.highlight}
    !sudo apt-get install ipython3-notebook python3-pip
:::
:::
:::

::: {.vbox .output_wrapper}
::: {.output .vbox}
::: {.hbox .output_area}
::: {.prompt}
:::

::: {.box-flex1 .output_subarea .output_stream .output_stdout}
    [sudo] password for notconfusing: 
:::
:::
:::
:::
:::

::: {.text_cell_render .border-box-sizing .rendered_html}
Some requirements of Wiki-class, including sklearn, and nltk, which are a pain with Python 3 since they haven't been properly packaged for it yet. So these you'll have to get from source:
:::

::: {.cell .border-box-sizing .code_cell .vbox}
::: {.input .hbox}
::: {.prompt .input_prompt}
In \[1\]:
:::

::: {.input_area .box-flex1}
::: {.highlight}
    !pip3 install git+https://github.com/scikit-learn/scikit-learn.git
    !pip3 install git+https://github.com/nltk/nltk/#
:::
:::
:::
:::

::: {.text_cell_render .border-box-sizing .rendered_html}
Making some random pages for a test dataset
-------------------------------------------

We'll need to get some Wikitext, with associated classifications, to start testing. I elected to make a random datasetin pywikibot, which as already stated is Python 2.7 only, and thus needs to be in a separate notebook, you can [view it on the nbviewer still](http://nbviewer.ipython.org/github/notconfusing/Wiki-Class/blob/master/Data%20Download%20Random%20Pages%20with%20Class%20python2.ipynb). Its output is a file `test_class_data.json` [(github link of the bzip)](https://github.com/notconfusing/Wiki-Class/blob/master/test_class_data.json.bz2) which is just a dictionary associating qualities and page-texts.

Warning, this dataset has some examples that can cause a `ZeroDivisonError` because some of these pages have 0 non-mark-up text. I wrote [this patch](https://github.com/halfak/Wiki-Class/pull/5) which fixes this issue.
:::

::: {.text_cell_render .border-box-sizing .rendered_html}
Testing the Pre-built Model
===========================
:::

::: {.cell .border-box-sizing .code_cell .vbox}
::: {.input .hbox}
::: {.prompt .input_prompt}
In \[3\]:
:::

::: {.input_area .box-flex1}
::: {.highlight}
    import json
    import pandas as pd
    from wikiclass.models import RFTextModel
:::
:::
:::

::: {.vbox .output_wrapper}
::: {.output .vbox}
::: {.hbox .output_area}
::: {.prompt}
:::

::: {.box-flex1 .output_subarea .output_stream .output_stderr}
    /usr/local/lib/python3.4/dist-packages/pandas/io/excel.py:626: UserWarning: Installed openpyxl is not supported at this time. Use >=1.6.1 and <2.0.0.
      .format(openpyxl_compat.start_ver, openpyxl_compat.stop_ver))
:::
:::
:::
:::
:::

::: {.text_cell_render .border-box-sizing .rendered_html}
Each model is stored in a `.model` file. A default one is included in the github repo.
:::

::: {.cell .border-box-sizing .code_cell .vbox}
::: {.input .hbox}
::: {.prompt .input_prompt}
In \[\]:
:::

::: {.input_area .box-flex1}
::: {.highlight}
    !wget https://github.com/halfak/Wiki-Class/blob/master/models/enwiki.rf_text.model?raw=true
:::
:::
:::
:::

::: {.cell .border-box-sizing .code_cell .vbox}
::: {.input .hbox}
::: {.prompt .input_prompt}
In \[35\]:
:::

::: {.input_area .box-flex1}
::: {.highlight}
    !mv enwiki.rf_text.model\?raw\=true enwiki.rf_text.model
:::
:::
:::
:::

::: {.text_cell_render .border-box-sizing .rendered_html}
Now we load the model.
:::

::: {.cell .border-box-sizing .code_cell .vbox}
::: {.input .hbox}
::: {.prompt .input_prompt}
In \[4\]:
:::

::: {.input_area .box-flex1}
::: {.highlight}
    model = RFTextModel.from_file(open("enwiki.rf_text.model",'rb'))
:::
:::
:::
:::

::: {.cell .border-box-sizing .code_cell .vbox}
::: {.input .hbox}
::: {.prompt .input_prompt}
In \[5\]:
:::

::: {.input_area .box-flex1}
::: {.highlight}
    classed_items = json.load(open('test_class_data.json','r'))
    print(sum([len(l) for l in classed_items.values()]))
:::
:::
:::

::: {.vbox .output_wrapper}
::: {.output .vbox}
::: {.hbox .output_area}
::: {.prompt}
:::

::: {.box-flex1 .output_subarea .output_stream .output_stdout}
    38959
:::
:::
:::
:::
:::

::: {.text_cell_render .border-box-sizing .rendered_html}
The Wiki-Class-provided model only deals with *'Stub', 'Start', 'B', 'C', 'Good Article'*, and *'Featured Article'* classifications. It does not include not *'List', 'Featured List',* or *'Disambig'* class pages. So we have to sort out the standard classes out of our 38,000 test articles.
:::

::: {.cell .border-box-sizing .code_cell .vbox}
::: {.input .hbox}
::: {.prompt .input_prompt}
In \[6\]:
:::

::: {.input_area .box-flex1}
::: {.highlight}
    standards = {actual: text for actual, text in classed_items.items() if actual in ['Stub', 'Start', 'C', 'B', 'GA', 'FA'] }
:::
:::
:::
:::

::: {.cell .border-box-sizing .code_cell .vbox}
::: {.input .hbox}
::: {.prompt .input_prompt}
In \[5\]:
:::

::: {.input_area .box-flex1}
::: {.highlight}
    print(sum([len(l) for l in standards.values()]))
:::
:::
:::

::: {.vbox .output_wrapper}
::: {.output .vbox}
::: {.hbox .output_area}
::: {.prompt}
:::

::: {.box-flex1 .output_subarea .output_stream .output_stdout}
    36873
:::
:::
:::
:::
:::

::: {.text_cell_render .border-box-sizing .rendered_html}
Now we iterate over our 36,000 standard-class pages, and put their Wiki-Class assessments into a DataFrame.
:::

::: {.cell .border-box-sizing .code_cell .vbox}
::: {.input .hbox}
::: {.prompt .input_prompt}
In \[6\]:
:::

::: {.input_area .box-flex1}
::: {.highlight}
    accuracy_df = pd.DataFrame(index=classed_items.keys(), columns=['actual','correct', 'model_prob', 'actual_prob'])
    for actual, text_list in standards.items():
        #see if actual is even here, otherwise no fair comparison
            for text in text_list:
                try:
                    assessment, probabilities = model.classify(text)
                except ZeroDivisionError:
                    continue
                    #print(actual, text)
                accuracy_df = accuracy_df.append({'actual': actual,
                                                  'correct':int(assessment == actual),
                                                  'model_prob': probabilities[assessment],
                                                  'actual_prob': probabilities[actual]}, ignore_index=True)
:::
:::
:::
:::

::: {.text_cell_render .border-box-sizing .rendered_html}
What you see here is that the output of an assessment is really two things. The *'assessment'* which is simply the *'class'* which the algorithm predicts best, but secondly a *dictionary of probablities* of how likely the text is to belong to each class.

In our DataFrame we record four data. The *'actual'* class as Wikipedia classes it; whether the actual class matches the model prediction. The probabilty (read: "confidence") of the model prediction. And lastly the probability of the actual class. Note in the "correct" case `model_prob` and `actual_prob` are the same.
:::

::: {.cell .border-box-sizing .code_cell .vbox}
::: {.input .hbox}
::: {.prompt .input_prompt}
In \[7\]:
:::

::: {.input_area .box-flex1}
::: {.highlight}
    df  = accuracy_df.dropna(how='all')
    df.head()
:::
:::
:::

::: {.vbox .output_wrapper}
::: {.output .vbox}
::: {.hbox .output_area}
::: {.prompt .output_prompt}
Out\[7\]:
:::

::: {.box-flex1 .output_subarea .output_pyout}
::: {.output_html .rendered_html}
::: {style="max-height: 1000px; max-width: 1500px; overflow: auto;"}
       actual   correct   model\_prob   actual\_prob
  ---- -------- --------- ------------- --------------
  18   Start    0         0.4           0.0
  19   Start    1         0.8           0.8
  20   Start    0         0.4           0.0
  21   Start    0         1.0           0.0
  22   Start    1         0.7           0.7
:::
:::
:::
:::
:::
:::
:::

::: {.text_cell_render .border-box-sizing .rendered_html}
If we look at the `correct` mean averages we should hopefully see something above 1/6th, which would be the performance of just guessing. Which we do.
:::

::: {.cell .border-box-sizing .code_cell .vbox}
::: {.input .hbox}
::: {.prompt .input_prompt}
In \[8\]:
:::

::: {.input_area .box-flex1}
::: {.highlight}
    groups = df.groupby(by='actual')
    groups['correct'].mean()
:::
:::
:::

::: {.vbox .output_wrapper}
::: {.output .vbox}
::: {.hbox .output_area}
::: {.prompt .output_prompt}
Out\[8\]:
:::

::: {.box-flex1 .output_subarea .output_pyout}
    actual
    B         0.247391
    C         0.278138
    FA        0.854167
    GA        0.444444
    Start     0.387334
    Stub      0.698394
    Name: correct, dtype: float64
:::
:::
:::
:::
:::

::: {.text_cell_render .border-box-sizing .rendered_html}
See how "close" predications are if they are not correct.
=========================================================
:::

::: {.text_cell_render .border-box-sizing .rendered_html}
Now we hack on the output. The Random Forest is really just binning text into difference classes, it doesn't know that some of the classes are closer to each other than others. Therefore we define a distance metric on the Standard Wiki classes. I call this order the *"Classic Order"* To get an intuition, consider this example. If an article is a *Good Aritcle* and the model prediction is also *Good Article* then it is off by 0; if the model prediction is *Featured Article* it is off off by 1; if the model prediction is *Start* then it was off by 3.
:::

::: {.cell .border-box-sizing .code_cell .vbox}
::: {.input .hbox}
::: {.prompt .input_prompt}
In \[7\]:
:::

::: {.input_area .box-flex1}
::: {.highlight}
    classic_order = ['Stub', 'Start', 'C', 'B', 'GA', 'FA']
    enum_classic = enumerate(classic_order)

    for enum, classic in dict(enum_classic).items():
        print(enum, classic)
:::
:::
:::

::: {.vbox .output_wrapper}
::: {.output .vbox}
::: {.hbox .output_area}
::: {.prompt}
:::

::: {.box-flex1 .output_subarea .output_stream .output_stdout}
    0 Stub
    1 Start
    2 C
    3 B
    4 GA
    5 FA
:::
:::
:::
:::
:::

::: {.text_cell_render .border-box-sizing .rendered_html}
Now we are going to iterate over the same dataset as above, but instead of recording "correctness", we record the closesness in a DataFrame.
:::

::: {.cell .border-box-sizing .code_cell .vbox}
::: {.input .hbox}
::: {.prompt .input_prompt}
In \[8\]:
:::

::: {.input_area .box-flex1}
::: {.highlight}
    classic_order = ['Stub', 'Start', 'C', 'B', 'GA', 'FA']
    classic_dict = dict(zip(classic_order, range(len(classic_order))))

    off_by_df = pd.DataFrame(index=classed_items.keys(), columns=['actual','off_by'])

    for classic in classic_order:
        for text in standards[classic]:
                try:
                    assessment, probabilities = model.classify(text)
                except ZeroDivisionError:
                    continue
                    #print(actual, text)
                off_by_df = off_by_df.append({'actual': classic,
                                                  'off_by':abs(classic_dict[assessment] - classic_dict[classic])}, ignore_index=True)
:::
:::
:::
:::

::: {.text_cell_render .border-box-sizing .rendered_html}
So it should look something like this as a table
:::

::: {.cell .border-box-sizing .code_cell .vbox}
::: {.input .hbox}
::: {.prompt .input_prompt}
In \[9\]:
:::

::: {.input_area .box-flex1}
::: {.highlight}
    off_by  = off_by_df.dropna(how='all')
    off_by.head()
:::
:::
:::

::: {.vbox .output_wrapper}
::: {.output .vbox}
::: {.hbox .output_area}
::: {.prompt .output_prompt}
Out\[9\]:
:::

::: {.box-flex1 .output_subarea .output_pyout}
::: {.output_html .rendered_html}
::: {style="max-height: 1000px; max-width: 1500px; overflow: auto;"}
       actual   off\_by
  ---- -------- ---------
  18   Stub     2
  19   Stub     1
  20   Stub     0
  21   Stub     0
  22   Stub     0
:::
:::
:::
:::
:::
:::
:::

::: {.text_cell_render .border-box-sizing .rendered_html}
And as a chart.
:::

::: {.cell .border-box-sizing .code_cell .vbox}
::: {.input .hbox}
::: {.prompt .input_prompt}
In \[10\]:
:::

::: {.input_area .box-flex1}
::: {.highlight}
    %pylab inline
:::
:::
:::

::: {.vbox .output_wrapper}
::: {.output .vbox}
::: {.hbox .output_area}
::: {.prompt}
:::

::: {.box-flex1 .output_subarea .output_stream .output_stdout}
    Populating the interactive namespace from numpy and matplotlib
:::
:::
:::
:::
:::

::: {.text_cell_render .border-box-sizing .rendered_html}
We can see that the middle classes are less easy to predict where as the ends are easier. This would corroborate our expectations. Since the the quality sprectrum bleed past these rather arbitrary cut-off points,ore of the quality specturm would lie in these intervals, and so its easier to bin them.
:::

::: {.cell .border-box-sizing .code_cell .vbox}
::: {.input .hbox}
::: {.prompt .input_prompt}
In \[11\]:
:::

::: {.input_area .box-flex1}
::: {.highlight}
    ax = off_by.groupby(by='actual',sort=False).mean().plot(title='Prediction Closeness by Quality Class', kind='bar', legend=False)
                                                       
    ax.set_ylabel('''Prediction Closeness (lower is more accurate)''')
    ax.set_xlabel('''Quality Class''')
:::
:::
:::

::: {.vbox .output_wrapper}
::: {.output .vbox}
::: {.hbox .output_area}
::: {.prompt .output_prompt}
Out\[11\]:
:::

::: {.box-flex1 .output_subarea .output_pyout}
    <matplotlib.text.Text at 0x7fc089810550>
:::
:::
:::
:::
:::

::: {.text_cell_render .border-box-sizing .rendered_html}
Making a model
==============
:::

::: {.text_cell_render .border-box-sizing .rendered_html}
Now we test the model-making feature. We will use our dataset of 'standards' from above, using a random 80% for training and 20% for testing.
:::

::: {.cell .border-box-sizing .code_cell .vbox}
::: {.input .hbox}
::: {.prompt .input_prompt}
In \[27\]:
:::

::: {.input_area .box-flex1}
::: {.highlight}
    from wikiclass.models import RFTextModel
    from wikiclass import assessments
:::
:::
:::
:::

::: {.text_cell_render .border-box-sizing .rendered_html}
Divvyig up our data into two lists.
:::

::: {.cell .border-box-sizing .code_cell .vbox}
::: {.input .hbox}
::: {.prompt .input_prompt}
In \[28\]:
:::

::: {.input_area .box-flex1}
::: {.highlight}
    import random

    train_set = list()
    test_set = list()
    for actual, text_list in standards.items():
        for text in text_list:
            if random.randint(0,9) >= 8:
                test_set.append( (text, actual) )
            else:
                train_set.append( (text, actual) )

    print(len(test_set)/len(train_set))
:::
:::
:::

::: {.vbox .output_wrapper}
::: {.output .vbox}
::: {.hbox .output_area}
::: {.prompt}
:::

::: {.box-flex1 .output_subarea .output_stream .output_stdout}
    0.2510772571506124
:::
:::
:::
:::
:::

::: {.text_cell_render .border-box-sizing .rendered_html}
And the next step is quite simple, we just click a button supplying our train\_set list, and test by supplying our test\_set list. Also the package conveniently supplies a saving function for us to store our model for later use.
:::

::: {.cell .border-box-sizing .code_cell .vbox}
::: {.input .hbox}
::: {.prompt .input_prompt}
In \[29\]:
:::

::: {.input_area .box-flex1}
::: {.highlight}
    # Train a model
    model = RFTextModel.train(
        train_set,
        assessments=assessments.WP10
    )

    # Run the test set & print the results
    results = model.test(test_set)
    print(results)

    # Write the model to disk for reuse.
    model.to_file(open("36K_random_enwiki.rf_text.model", "wb"))
:::
:::
:::

::: {.vbox .output_wrapper}
::: {.output .vbox}
::: {.hbox .output_area}
::: {.prompt}
:::

::: {.box-flex1 .output_subarea .output_stream .output_stdout}
    pred assessment    B    C  FA  GA  Start  Stub
    real assessment                               
    B                130   29   1   5    105    40
    C                 34  112   0   2    151    33
    FA                 7    3   4   0      1     0
    GA                 8    8   0  11      9     1
    Start             80   87   0   2   1420   525
    Stub              40   32   0   0    547  3973
:::
:::
:::
:::
:::

::: {.text_cell_render .border-box-sizing .rendered_html}
Now to look at accuracy, we norm the DataFrame row-wise.
:::

::: {.cell .border-box-sizing .code_cell .vbox}
::: {.input .hbox}
::: {.prompt .input_prompt}
In \[30\]:
:::

::: {.input_area .box-flex1}
::: {.highlight}
    norm_results = results.apply(lambda col: col / col.sum(), axis=1)
    norm_results
:::
:::
:::

::: {.vbox .output_wrapper}
::: {.output .vbox}
::: {.hbox .output_area}
::: {.prompt .output_prompt}
Out\[30\]:
:::

::: {.box-flex1 .output_subarea .output_pyout}
::: {.output_html .rendered_html}
::: {style="max-height: 1000px; max-width: 1500px; overflow: auto;"}

<table class="dataframe" border="1">


<thead>


<tr style="text-align: right;">


<th>

pred assessment
:::
:::
:::
:::
:::
:::
:::


</th>


<th>

B


</th>


<th>

C


</th>


<th>

FA


</th>


<th>

GA


</th>


<th>

Start


</th>


<th>

Stub


</th>


</tr>


<tr>


<th>

real assessment


</th>


<th>


</th>


<th>


</th>


<th>


</th>


<th>


</th>


<th>


</th>


<th>


</th>


</tr>


</thead>


<tbody>


<tr>


<th>

B


</th>


<td>

0.419355


</td>


<td>

0.093548


</td>


<td>

0.003226


</td>


<td>

0.016129


</td>


<td>

0.338710


</td>


<td>

0.129032


</td>


</tr>


<tr>


<th>

C


</th>


<td>

0.102410


</td>


<td>

0.337349


</td>


<td>

0.000000


</td>


<td>

0.006024


</td>


<td>

0.454819


</td>


<td>

0.099398


</td>


</tr>


<tr>


<th>

FA


</th>


<td>

0.466667


</td>


<td>

0.200000


</td>


<td>

0.266667


</td>


<td>

0.000000


</td>


<td>

0.066667


</td>


<td>

0.000000


</td>


</tr>


<tr>


<th>

GA


</th>


<td>

0.216216


</td>


<td>

0.216216


</td>


<td>

0.000000


</td>


<td>

0.297297


</td>


<td>

0.243243


</td>


<td>

0.027027


</td>


</tr>


<tr>


<th>

Start


</th>


<td>

0.037843


</td>


<td>

0.041154


</td>


<td>

0.000000


</td>


<td>

0.000946


</td>


<td>

0.671712


</td>


<td>

0.248344


</td>


</tr>


<tr>


<th>

Stub


</th>


<td>

0.008711


</td>


<td>

0.006969


</td>


<td>

0.000000


</td>


<td>

0.000000


</td>


<td>

0.119120


</td>


<td>

0.865200


</td>


</tr>


</tbody>


</table>


</div>


</div>


</div>


</div>


</div>


</div>


</div>

::: {.text_cell_render .border-box-sizing .rendered_html}
And finally we can view the peformance by class, which intriguingly seems to be better than what we got with the batteries-included model.
:::

::: {.cell .border-box-sizing .code_cell .vbox}
::: {.input .hbox}
::: {.prompt .input_prompt}
In \[35\]:
:::

::: {.input_area .box-flex1}
::: {.highlight}
    for c in classic_order:
        print(c, norm_results.loc[c][c])
:::
:::
:::

::: {.vbox .output_wrapper}
::: {.output .vbox}
::: {.hbox .output_area}
::: {.prompt}
:::

::: {.box-flex1 .output_subarea .output_stream .output_stdout}
    Stub 0.865200348432
    Start 0.671712393567
    C 0.33734939759
    B 0.41935483871
    GA 0.297297297297
    FA 0.266666666667
:::
:::
:::
:::
:::

::: {.text_cell_render .border-box-sizing .rendered_html}
We can see that, having a large number of stubs to train on really gives us a high precision in classifying them.

So there you have it - a brief playing around with Wiki-Class, an easy way to get rough quality estimates out of your data. If you extend any more examples of using this class, I'd be intrigued to see and collaborate on them.

‽[\[\@notconusing\]]{.citation}(https://twitter.com/notconfusing)
:::

::: {.cell .border-box-sizing .code_cell .vbox}
::: {.input .hbox}
::: {.prompt .input_prompt}
In \[\]:
:::

::: {.input_area .box-flex1}
:::
:::
:::
