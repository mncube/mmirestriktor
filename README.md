
<!-- README.md is generated from README.Rmd. Please edit that file -->

# mmirestriktor

<!-- badges: start -->
<!-- badges: end -->

The goal of the Mighty Metrika Interface to Restriktor (‘mmirestriktor’)
R package is to provide ‘shiny’ web applications built on top of
[‘restriktor’](https://restriktor.org/) and to provide tools for
building ‘shiny’ applications which use ‘restriktor’.

## Installation

You can install the released version of ‘mmirestriktor’ from
[CRAN](https://CRAN.R-project.org):

``` r
install.packages("mmirestriktor")
```

To install the development version of ‘mmirestriktor’ from GitHub, use
the [devtools](https://devtools.r-lib.org/) package:

``` r
# install.packages("devtools")
devtools::install_github("mightymetrika/mmirestriktor")
```

## Analyze Your Data

Use the mmirestriktor() function to launch a ‘shiny’ application which
runs informative hypothesis testing via restriktor::iht() and estimation
of restricted estimates via restriktor::restriktor().

The application has the following functionalities:

- Upload a CSV file to be used as the dataset for modeling.
- View the variables available in the uploaded dataset.
- Input a formula to define the model to be fit.
- Choose a model fitting engine from “lm”, “glm”, and “rlm”.
- Pass extra arguments to the model fitting function.
- View the terms available for defining constraints after fitting the
  model.
- Define constraints for hypothesis testing.
- Set a significance level (alpha) for hypothesis testing.
- Choose the type of analysis to perform: Informative Hypothesis Test
  and/or Restricted Means.
- View the results and interpretation

This version does not allow you to pass additional arguments to
restriktor::iht() or to restriktor::restriktor(). As such, you will need
to run the ‘restriktor’ package in R to access additional capabilities.

``` r
library(mmirestriktor)

# Launch application
mmirestriktor()
```

## Play FbarCards

FbarCards is a card game that comes with ‘mmirestriktor’. In this game,
a grid of cards is displayed and the objective is to reorder the cards
in each row such that, when the rows are stacked, the columns of cards
are in increasing order from left to right.

To play this game you:

1)  Choose a difficulty level n (from n = 3 to n = 7)
2)  Click Start Game to deal an n x n grid of cards from a 52 card
    standard deck
3)  Within each row you can either swap 2 cards or leave the row as is
4)  Click Score Game

To score the game, the final card grid is pivoted to a long form
dataframe with the variables Value (the value of each card) and Column
(the cards column number on the final grid). Column is treated as a
factor variable in a stats::lm() model with the formula:

formula = Value \~ -1 + Column

If, for example, the game was set to n = 4, then the informative
hypothesis testing constraint would be:

‘Column1 \< Column2 \< Column3 \< Column4’

You win if the order-constrained hypothesis is supported and you lose if
the order-constrained hypothesis is not supported. The iht_interpreter()
function is incorporated into the game in order to help interpret the
results in terms of the Type B and Type A hypothesis tests.

``` r
FbarCards()
```

# References

Vanbrabant, L., & Rosseel, Y. (2020). An Introduction to Restriktor:
Evaluating informative hypotheses for linear models. In R. van de Schoot
& M. Miocevic (Eds.), Small Sample Size Solutions: A Guide for Applied
Researchers and Practitioners (1st ed., pp. 157 -172). Routledge.
<https://doi.org/10.4324/9780429273872-14>
