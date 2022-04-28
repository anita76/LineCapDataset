# LineCap Dataset

This repository contains the figures and annotations for LineCap, a dataset of line charts scraped from scientific figures each accompanied with a crowd-sourced caption describing the trends of individual lines in the figure.

The collected annotations are saved in `csv` files with the following columns:

* `image`: name of corresponding image file
* `num_lines`: number of line plots in the figure (1 to 5)
* `trend_1`: description of line 1's trend
* `trend_2`: description of line 2's trend
* `trend_3`: description of line 3's trend
* `trend_4`: description of line 4's trend
* `trend_5`: description of line 5's trend
* `trend_overall`: description of the overall figure trend

`<data_split>_no_values.csv` does not include any references to x and y values read from the figure. It replaces any references to these values in the trend descriptions with the token `_value_`.

## Special Tokens

LineCap uses special tokens to refer to axis and line labels:
* `xlabel`: this token is used to refer to the x-axis label. 
* `ylabel`: this token is used to refer to the y-axis label. 
* `Line n`: lines are referred to by their number (1 to 5) instead of their labels.

The green text in the figure below shows how special tokens substitute references to line and axis labels in this dataset.

<img src="/instruction_imgs/special-tokens.jpg?raw=true" alt="Use of special tokens to replace line and axis labels" style="width:600px;"/>

### Line Numbering Rules

1. The lines are numbered from top to bottom based on the order of their label in the figure legend.

<img src="/instruction_imgs/top-to-bottom.jpg?raw=true" alt="Figure showing lines numbered from top to bottom in the legend" style="width:600px;"/>

2. In case of ties (i.e. when two line labels appear to be at the same height), lines are numbered from left to right then top to bottom. For example, in the figure below, the labels of the cubic and linear lines are at the same height in the legend. The cubic line is further to the left, therefore it is line 1 while the linear line is line 2.

<img src="/instruction_imgs/left-to-right.jpg?raw=true" alt="Figure showing lines numbered from left to right in the legend when there is a tie" style="width:600px;"/>

3. If the figure lines are labeled directly in the chart instead of a legend, we use the labels within the chart to number the lines from top to bottom and in case of ties from left to right. In the figure below, for example, the lines are directly labeled with arrows in the chart. The `Optimal code` line's label is at the top of the chart, therefore it is numbered as line 1. The `Extrapolated performance of the decoder` line has the second highest label in the chart, therefore it is line 2 while the `Outer bound` line is line 3 and the `Uncoded transmission` line is line 4.

<img src="/instruction_imgs/labels-only.jpg?raw=true" alt="Figure with lines labeled directly in the chart" style="width:600px;"/>

4. If the figure lines are labeled both directly in the chart and in a legend, the legend is used for ordering the lines. For instance, in the figure below, the lines are labeled both in the chart with arrows and in the legend. The line orders in the chart and the legend do not match. In the chart, the `approximated-MDP` line has the second highest label but in the legend, the `Lyapunov` line has the highest label. The lines should be numbered based on the legend in such cases. As such, the `Lyapunov` line is line 2 while the `approximated-MDP` line is line 3.

<img src="/instruction_imgs/repeated-labels.jpg?raw=true" alt="Figure with labels both in the chart and the legend" style="width:600px;"/>


## License

LineCap is for non-commercial use only and is released under [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/). You agree to the terms of this license by using this dataset.

The figure images in LineCap are from [SciCap](https://github.com/tingyaohsu/SciCap) which is a dataset released under [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/).

