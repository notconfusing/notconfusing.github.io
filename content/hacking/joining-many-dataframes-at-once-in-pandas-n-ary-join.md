Title: Joining many DataFrames at once in Pandas: "n-ary Join"
Date: 2015-02-11 19:28
Author: max
Category: hacking
Slug: joining-many-dataframes-at-once-in-pandas-n-ary-join
Status: published

::: {.cell .border-box-sizing .text_cell .rendered}
::: {.prompt .input_prompt}
:::

::: {.inner_cell}
::: {.text_cell_render .border-box-sizing .rendered_html}
Joining many DataFrames at once with Reduce
===========================================

In my last project I wanted to compare many different Gender Inequality Indexes at once, including the one I had just come up with, called ["WIGI"](http://notconfusing.com/preliminary-results-from-wigi-the-wikipedia-gender-inequality-index/ "Preliminary Results From WIGI, The Wikipedia Gender Inequality Index"). The problem was that the rank and score data for each index was in a separate DataFrame. I need to perform repeated SQL-style `join`s. In this case I actually only had to join 5 dataframes, for 5 indices. But later, in helping my partner with her research, she came across the same problem needed to join more than 100. In my mind I saw that we wanted to accomplish this n-ary join. Mathematically I wanted this type of operation, which I couldn't find in `pandas`. [![join]({static}/images/uploads/2015/02/join.jpg){.aligncenter .wp-image-3729 .size-medium style="width:300px !important"}]({static}/images/uploads/2015/02/join.jpg)

The answer I enjoyed implementing, perhaps because I saw it as this type of repeated operation, is the `reduce` of functional programming.

Ok, say we have these two data sets:
:::
:::
:::

::: {.cell .border-box-sizing .code_cell .rendered}
::: {.input}
::: {.prompt .input_prompt}
In \[5\]:
:::

::: {.inner_cell}
::: {.input_area}
::: {.highlight}
    wigi
:::
:::
:::
:::

::: {.output_wrapper}
::: {.output}
::: {.output_area}
::: {.prompt .output_prompt}
Out\[5\]:
:::

::: {.output_html .rendered_html .output_subarea .output_pyout}
::: {style="max-height: 1000px; max-width: 1500px; overflow: auto;"}

<table class="dataframe" border="1">


<thead>


<tr style="text-align: right;">


<th>

:::
:::
:::
:::
:::
:::


</th>


<th>

Rank

</th>


<th>

Score

</th>


</tr>


<tr>


<th>

Economy

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

Republic of China

</th>


<td>

1

</td>


<td>

0.356890

</td>


</tr>


<tr>


<th>

Kingdom of Denmark

</th>


<td>

2

</td>


<td>

0.347826

</td>


</tr>


<tr>


<th>

Sweden

</th>


<td>

3

</td>


<td>

0.345212

</td>


</tr>


<tr>


<th>

South Korea

</th>


<td>

4

</td>


<td>

0.343662

</td>


</tr>


<tr>


<th>

Hong Kong

</th>


<td>

5

</td>


<td>

0.342857

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

::: {.cell .border-box-sizing .code_cell .rendered}
::: {.input}
::: {.prompt .input_prompt}
In \[6\]:
:::

::: {.inner_cell}
::: {.input_area}
::: {.highlight}
    world_economic_forum
:::
:::
:::
:::

::: {.output_wrapper}
::: {.output}
::: {.output_area}
::: {.prompt .output_prompt}
Out\[6\]:
:::

::: {.output_html .rendered_html .output_subarea .output_pyout}
::: {style="max-height: 1000px; max-width: 1500px; overflow: auto;"}

<table class="dataframe" border="1">


<thead>


<tr style="text-align: right;">


<th>

:::
:::
:::
:::
:::
:::


</th>


<th>

Rank

</th>


<th>

Score

</th>


</tr>


<tr>


<th>

Economy

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

Iceland

</th>


<td>

1

</td>


<td>

0.8594

</td>


</tr>


<tr>


<th>

Finland

</th>


<td>

2

</td>


<td>

0.8453

</td>


</tr>


<tr>


<th>

Norway

</th>


<td>

3

</td>


<td>

0.8374

</td>


</tr>


<tr>


<th>

Sweden

</th>


<td>

4

</td>


<td>

0.8165

</td>


</tr>


<tr>


<th>

Denmark

</th>


<td>

5

</td>


<td>

0.8025

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

::: {.cell .border-box-sizing .text_cell .rendered}
::: {.prompt .input_prompt}
:::

::: {.inner_cell}
::: {.text_cell_render .border-box-sizing .rendered_html}
We'd probably join them like this:
:::
:::
:::

::: {.cell .border-box-sizing .code_cell .rendered}
::: {.input}
::: {.prompt .input_prompt}
In \[7\]:
:::

::: {.inner_cell}
::: {.input_area}
::: {.highlight}
    wigi.join(world_economic_forum, how='outer', lsuffix='_wigi', rsuffix='_wef')
:::
:::
:::
:::

::: {.output_wrapper}
::: {.output}
::: {.output_area}
::: {.prompt .output_prompt}
Out\[7\]:
:::

::: {.output_html .rendered_html .output_subarea .output_pyout}
::: {style="max-height: 1000px; max-width: 1500px; overflow: auto;"}

<table class="dataframe" border="1">


<thead>


<tr style="text-align: right;">


<th>

:::
:::
:::
:::
:::
:::


</th>


<th>

Rank_wigi

</th>


<th>

Score_wigi

</th>


<th>

Rank_wef

</th>


<th>

Score_wef

</th>


</tr>


<tr>


<th>

Economy

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

Denmark

</th>


<td>

NaN

</td>


<td>

NaN

</td>


<td>

5

</td>


<td>

0.8025

</td>


</tr>


<tr>


<th>

Finland

</th>


<td>

NaN

</td>


<td>

NaN

</td>


<td>

2

</td>


<td>

0.8453

</td>


</tr>


<tr>


<th>

Hong Kong

</th>


<td>

5

</td>


<td>

0.342857

</td>


<td>

NaN

</td>


<td>

NaN

</td>


</tr>


<tr>


<th>

Iceland

</th>


<td>

NaN

</td>


<td>

NaN

</td>


<td>

1

</td>


<td>

0.8594

</td>


</tr>


<tr>


<th>

Kingdom of Denmark

</th>


<td>

2

</td>


<td>

0.347826

</td>


<td>

NaN

</td>


<td>

NaN

</td>


</tr>


<tr>


<th>

Norway

</th>


<td>

NaN

</td>


<td>

NaN

</td>


<td>

3

</td>


<td>

0.8374

</td>


</tr>


<tr>


<th>

Republic of China

</th>


<td>

1

</td>


<td>

0.356890

</td>


<td>

NaN

</td>


<td>

NaN

</td>


</tr>


<tr>


<th>

South Korea

</th>


<td>

4

</td>


<td>

0.343662

</td>


<td>

NaN

</td>


<td>

NaN

</td>


</tr>


<tr>


<th>

Sweden

</th>


<td>

3

</td>


<td>

0.345212

</td>


<td>

4

</td>


<td>

0.8165

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

::: {.cell .border-box-sizing .text_cell .rendered}
::: {.prompt .input_prompt}
:::

::: {.inner_cell}
::: {.text_cell_render .border-box-sizing .rendered_html}
But we want to generalize. Notice here we also inject the name of the DataFrame into the column names to avoid "suffix-hell" as I would like to term it.
:::
:::
:::

::: {.cell .border-box-sizing .code_cell .rendered}
::: {.input}
::: {.prompt .input_prompt}
In \[1\]:
:::

::: {.inner_cell}
::: {.input_area}
::: {.highlight}
    import pandas

    def make_df(filename):
        df = pandas.DataFrame.from_csv(filename)
        name = filename.split('.')[0]
        df.columns = map(lambda col: '{}_{}'.format(str(col), name), df.columns)
        return df

    filenames = !ls

    dfs = [make_df(filename) for filename in filenames]
:::
:::
:::
:::
:::

::: {.cell .border-box-sizing .text_cell .rendered}
::: {.prompt .input_prompt}
:::

::: {.inner_cell}
::: {.text_cell_render .border-box-sizing .rendered_html}
Now here's the reducer. I actually end up wanting an inner join in the end, but the type of join is not important to illustrate the fact.

Here we join 5 DataFrames at once.
:::
:::
:::

::: {.cell .border-box-sizing .code_cell .rendered}
::: {.input}
::: {.prompt .input_prompt}
In \[2\]:
:::

::: {.inner_cell}
::: {.input_area}
::: {.highlight}
    def join_dfs(ldf, rdf):
        return ldf.join(rdf, how='inner')

    final_df = reduce(join_dfs, dfs) #that's the magic
    final_df.head()
:::
:::
:::
:::

::: {.output_wrapper}
::: {.output}
::: {.output_area}
::: {.prompt .output_prompt}
Out\[2\]:
:::

::: {.output_html .rendered_html .output_subarea .output_pyout}
::: {style="max-height: 1000px; max-width: 1500px; overflow: auto;"}

<table class="dataframe" border="1">


<thead>


<tr style="text-align: right;">


<th>

:::
:::
:::
:::
:::
:::


</th>


<th>

Score_gdi

</th>


<th>

Rank_gdi

</th>


<th>

Score_gei

</th>


<th>

Rank_gei

</th>


<th>

Rank_sigi

</th>


<th>

Score_sigi

</th>


<th>

Rank_wdf

</th>


<th>

Score_wdf

</th>


<th>

Rank_wef

</th>


<th>

Score_wef

</th>


</tr>


<tr>


<th>

Economy

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

Nicaragua

</th>


<td>

0.912

</td>


<td>

102

</td>


<td>

74

</td>


<td>

37

</td>


<td>

53

</td>


<td>

0.8405

</td>


<td>

13

</td>


<td>

0.272727

</td>


<td>

6

</td>


<td>

0.7894

</td>


</tr>


<tr>


<th>

Rwanda

</th>


<td>

0.950

</td>


<td>

80

</td>


<td>

77

</td>


<td>

19

</td>


<td>

43

</td>


<td>

0.8661

</td>


<td>

134

</td>


<td>

0.096154

</td>


<td>

7

</td>


<td>

0.7854

</td>


</tr>


<tr>


<th>

Philippines

</th>


<td>

0.989

</td>


<td>

17

</td>


<td>

76

</td>


<td>

26

</td>


<td>

57

</td>


<td>

0.8235

</td>


<td>

6

</td>


<td>

0.322785

</td>


<td>

9

</td>


<td>

0.7814

</td>


</tr>


<tr>


<th>

Belgium

</th>


<td>

0.977

</td>


<td>

38

</td>


<td>

79

</td>


<td>

12

</td>


<td>

1

</td>


<td>

0.9984

</td>


<td>

73

</td>


<td>

0.163734

</td>


<td>

10

</td>


<td>

0.7809

</td>


</tr>


<tr>


<th>

Latvia

</th>


<td>

1.033

</td>


<td>

52

</td>


<td>

77

</td>


<td>

19

</td>


<td>

24

</td>


<td>

0.9489

</td>


<td>

82

</td>


<td>

0.157623

</td>


<td>

15

</td>


<td>

0.7691

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

::: {.cell .border-box-sizing .text_cell .rendered}
::: {.prompt .input_prompt}
:::

::: {.inner_cell}
::: {.text_cell_render .border-box-sizing .rendered_html}
I really like the elegance of this solution. I admit there may be other ways to go about it with `pandas` only, and I understand the `R` mentality of "no for loops". Still this is precisely why I like `pandas` in python - you still get the freedom to play as you wish if it makes more sense to you.
:::
:::
:::
