
<!-- README.md is generated from README.Rmd. Please edit that file -->

# ANTTV

<!-- badges: start -->

<!-- badges: end -->

ANTTV provides methods for analysing data that represents textual
variation in the New Testament. The New Testament, like all other works
that have been through a hand-copying phase, exhibits textual variation.
For instance, the apparatus of the 5th edition of the United Bible
Societies *Greek New Testament* gives these readings and attestations at
Mark 1.1:

1.  Χριστου υιου θεου: Aleph-1, B, D, L, W
2.  Χριστου υιου του θεου: A, Delta, fam-1, fam-13, 33, 180, …
3.  Χριστου υιου του κυριου: 1241
4.  Χριστου: Aleph-\*, Theta, 28-c, syr-pal, …
5.  omit: 28-\*

Five different readings are listed. (Accents are omitted here.) The
attestations follow colons on each line and identify the witnesses
(i.e. manuscripts, lectionaries, versions, patristic citations) that
support each reading.

A *data frame* (i.e. table) can be constructed with rows corresponding
to witnesses and columns corresponding to variation sites such as the
one just given. The cell addressed by a particular row and column
contains a code representing the reading of that witness at that
variation site. For example, if the numerals given in the above list of
readings are used as codes, the value entered in the cell at the
intersection of row *Theta* and column *Mark 1.1* would be *4*. Please
note that here (i.e. in this package) the same codes (typically
numerals) are reused at other variation sites, each variation site has
its own correspondence between codes and readings, and no association is
implied by the same code being used at two different variation sites.

Analysis can begin with the data frame itself or with a *distance
matrix* constructed by calculating distances between witnesses in the
data frame. The *simple matching distance* is used here, being the
number of places where the readings of two witnesses differ divided by
the number of places where the readings of the two can be compared
(i.e. are defined). The analysis methods used here usually begin with a
distance matrix calculated from a data frame.

## Installation

You can install the development version of ANTTV from
[GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("tjfinney/ANTTV")
```

## Usage

A fairly common task when dealing with strings is the need to split a
single string into many parts. This is what `base::strsplit()` and
`stringr::str_split()` do.

``` r
(x <- "alfa,bravo,charlie,delta")
#> [1] "alfa,bravo,charlie,delta"
strsplit(x, split = ",")
#> [[1]]
#> [1] "alfa"    "bravo"   "charlie" "delta"
stringr::str_split(x, pattern = ",")
#> [[1]]
#> [1] "alfa"    "bravo"   "charlie" "delta"
```

Notice how the return value is a **list** of length one, where the first
element holds the character vector of parts. Often the shape of this
output is inconvenient, i.e. we want the un-listed version. That’s
exactly what `ANTTV::str_split_one()` does.

``` r
library(ANTTV)

str_split_one(x, pattern = ",")
#> [1] "alfa"    "bravo"   "charlie" "delta"
```

Use `str_split_one()` when the input is known to be a single string. For
safety, it will error if its input has length greater than one.
`str_split_one()` is built on `stringr::str_split()`, so you can use its
`n` argument and stringr’s general interface for describing the
`pattern` to be matched.

``` r
str_split_one(x, pattern = ",", n = 2)
#> [1] "alfa"                "bravo,charlie,delta"

y <- "192.168.0.1"
str_split_one(y, pattern = stringr::fixed("."))
#> [1] "192" "168" "0"   "1"
```

## Example

This is a basic example which shows you how to solve a common problem:

``` r
library(ANTTV)
## basic example code
```

What is special about using `README.Rmd` instead of just `README.md`?
You can include R chunks like so:

``` r
summary(cars)
#>      speed           dist       
#>  Min.   : 4.0   Min.   :  2.00  
#>  1st Qu.:12.0   1st Qu.: 26.00  
#>  Median :15.0   Median : 36.00  
#>  Mean   :15.4   Mean   : 42.98  
#>  3rd Qu.:19.0   3rd Qu.: 56.00  
#>  Max.   :25.0   Max.   :120.00
```

You’ll still need to render `README.Rmd` regularly, to keep `README.md`
up-to-date. `devtools::build_readme()` is handy for this. You could also
use GitHub Actions to re-render `README.Rmd` every time you push. An
example workflow can be found here:
<https://github.com/r-lib/actions/tree/v1/examples>.

You can also embed plots, for example:

<img src="man/figures/README-pressure-1.png" width="100%" />

In that case, don’t forget to commit and push the resulting figure
files, so they display on GitHub and CRAN.