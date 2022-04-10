# LineCapDataset

This repository contains the figures and annotations for the LineCap dataset.

The collected annotations are saved in `csv` files with the following columns:

* `image`: name of corresponding image file
* `num_lines`: number of line plots in the figure
* `trend_1`: description of line 1's trend
* `trend_2`: description of line 2's trend
* `trend_3`: description of line 3's trend
* `trend_4`: description of line 4's trend
* `trend_5`: description of line 5's trend
* `trend_overall`: description of the overall figure trend

`labels_no_values.csv` does not include any references to x and y values read from the figure. It replaces any references to these values in the trend descriptions with the token `_value_`.
