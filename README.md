
<!-- README.md is generated from README.Rmd. Please edit that file -->

# ANTTV

<!-- badges: start -->
<!-- badges: end -->

ANTTV is a suite of R programs to analyse data on New Testament textual
variation. It uses the R pipe operator `|>` to chain together functions
to produce analysis results.

To get started:

1.  Install R on your computer
2.  \[Optional\] To make life far easier, install RStudio on your
    computer
3.  Install the ANTTV package
4.  Use the programs in the package to analyse the data.

## Installation

You can install the development version of ANTTV from
[GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("tjfinney/ANTTV")
```

Installing the *ape* and *rgl* packages can be challenging as additional
software may need to be installed on your operating system. Details will
vary according to your platform (whether Linux, Mac, or Windows).
Looking at the package documentation is a good place to start:

- <http://ape-package.ird.fr/ape_installation.html>
- <https://dmurdoch.github.io/rgl/>

The following notes (specific to Ubuntu Linux) might help too.

### Install ape package

If you hit errors like
`/usr/bin/ld: cannot find -llapack: No such file or directory` then try
installing `gfortran`, `blas`, and `lapack` with
`sudo apt install gfortran libblas-dev liblapack-dev`.

### Install software for do_CMDS()

`do_CMDS()` didn’t work with the default `rgl` installation. The
following steps were required to get it working:

1.  Install OpenGL support (on Linux):
    `sudo apt install libgl1-mesa-dev libglu1-mesa-dev`
2.  Install dev version of `rgl` package in RStudio:
    `remotes::install_github("dmurdoch/rgl")`
3.  Install Magick++ (on Linux): `sudo apt install libmagick++-dev`
4.  Install `magick` package in RStudio: `install.packages("magick")`
5.  Install ImageMagick (on Linux): `sudo apt install imagemagick`

## Examples

To analyse a data frame,

    read_data_frame("https://zenodo.org/record/6466262/files/Mark.UBS4.csv") |> do_reduction() |> do_dist() |> do_CMDS()

``` r
library(ANTTV)
## read data frame, do data reduction, do distance matrix, do classical scaling
read_data_frame("https://zenodo.org/record/6466262/files/Mark.UBS4.csv") |> do_reduction() |> do_dist() |> do_CMDS()
#> $points
#>                   [,1]         [,2]         [,3]
#> UBS       -0.318972971  0.194270665 -0.094895228
#> Aleph     -0.402898198  0.269525073 -0.082953043
#> A          0.194079913  0.067214714 -0.029144244
#> B         -0.407695718  0.302783611 -0.082224628
#> C         -0.070565268  0.216311931 -0.126523956
#> D         -0.213244810 -0.394572383 -0.065499779
#> L         -0.270332112  0.308817774  0.002019480
#> W         -0.215353197 -0.024605019  0.236818508
#> Delta     -0.193340862  0.270585309 -0.031450623
#> Theta     -0.053043344 -0.166354680  0.168556394
#> Psi       -0.294980231  0.335557245  0.022878930
#> f-1        0.029279465  0.032905886  0.249578586
#> f-13       0.131812026 -0.025615430  0.183325399
#> 28         0.003363116  0.018867415  0.235471518
#> 33         0.096235710  0.121991274 -0.057058006
#> 157        0.194558513  0.043918917 -0.046976706
#> 180        0.226756291  0.034800290 -0.041628692
#> 205        0.023512414  0.027871047  0.234254673
#> 565       -0.083902027 -0.122987116  0.230830263
#> 579        0.042261931  0.104377608 -0.039595228
#> 597        0.208740842  0.050555389 -0.032566831
#> 700        0.086802252 -0.052303212  0.092887828
#> 892       -0.081967150  0.259646842 -0.072922633
#> 1006       0.217672478  0.057258192 -0.026337106
#> 1010       0.224967491  0.051950264 -0.037056390
#> 1071       0.203171780  0.054837268  0.009825480
#> 1241       0.187674495  0.074936427 -0.017185244
#> 1243       0.194638988  0.035762396  0.011607454
#> 1292       0.211727191  0.064310759 -0.028037394
#> 1342      -0.018653021  0.165134170 -0.093805800
#> 1424       0.180495281  0.076938650  0.027964107
#> 1505       0.229027599  0.072527817 -0.013039821
#> 2427      -0.282079045  0.246606711 -0.131204627
#> Byz        0.220975734  0.047524270 -0.030897012
#> E          0.223638711  0.049012838 -0.047380860
#> F          0.243191771  0.048159993 -0.040713971
#> G          0.198338404  0.059288163  0.005171776
#> H          0.233519847  0.050164510 -0.053665925
#> N          0.220950026 -0.005706080 -0.130779060
#> Sigma      0.203177108  0.037280120 -0.009572371
#> Lect       0.197418676  0.058640329  0.009892348
#> it-a      -0.111022827 -0.391193407 -0.110902686
#> it-aur     0.002804504 -0.152556472 -0.089856709
#> it-b      -0.181911699 -0.404718030 -0.006874633
#> it-c      -0.144232189 -0.245167086 -0.106351065
#> it-d      -0.201416638 -0.410229304 -0.128001934
#> it-f       0.047199739 -0.117741439 -0.110339246
#> it-ff-2   -0.152219756 -0.353069966 -0.095206847
#> it-i      -0.073766302 -0.374332869 -0.023081359
#> it-k      -0.527762585 -0.100218862 -0.049500611
#> it-l       0.006820806 -0.108863005 -0.081845853
#> it-q       0.043447849 -0.221243223 -0.044162011
#> it-r-1    -0.081276366 -0.348887639 -0.106700498
#> vg         0.011769695 -0.114070290 -0.093940192
#> syr-p      0.112285962 -0.007267304 -0.005765008
#> syr-h      0.210948418  0.035090763 -0.019698910
#> syr-pal    0.015456990  0.001140513  0.076210171
#> syr-s     -0.209371793 -0.043999866  0.278618333
#> cop-sa    -0.276507992  0.192652004  0.016534407
#> cop-bo    -0.236880248  0.193498882 -0.069616736
#> arm       -0.101254903 -0.054258919  0.306600948
#> eth        0.027477866  0.068007920 -0.073945748
#> geo       -0.064532442 -0.022293452  0.304487875
#> slav       0.142064034  0.015601052 -0.005607064
#> Augustine  0.020919779 -0.154069944 -0.019022189
#> 
#> $eig
#>  [1]  2.446528e+00  2.137842e+00  8.512329e-01  4.596134e-01  4.193191e-01
#>  [6]  3.140997e-01  3.040783e-01  2.354431e-01  2.110081e-01  2.100776e-01
#> [11]  1.939429e-01  1.772375e-01  1.550375e-01  1.489006e-01  1.252941e-01
#> [16]  1.116424e-01  1.093717e-01  9.750911e-02  8.045907e-02  7.430312e-02
#> [21]  7.139100e-02  5.940155e-02  5.481080e-02  4.636929e-02  4.117961e-02
#> [26]  3.685747e-02  3.137585e-02  3.024420e-02  2.800779e-02  2.367259e-02
#> [31]  1.702126e-02  1.461860e-02  1.194273e-02  6.044219e-03  5.079421e-03
#> [36]  2.452274e-03  1.750304e-03  3.885781e-16 -1.073112e-03 -1.940503e-03
#> [41] -2.592090e-03 -3.282169e-03 -8.548371e-03 -9.951507e-03 -1.247874e-02
#> [46] -1.354019e-02 -1.551074e-02 -1.617091e-02 -2.190334e-02 -3.020265e-02
#> [51] -3.103579e-02 -3.435256e-02 -3.699214e-02 -3.809257e-02 -4.254562e-02
#> [56] -4.859081e-02 -5.778687e-02 -6.571772e-02 -7.212038e-02 -8.390071e-02
#> [61] -9.887854e-02 -1.128535e-01 -1.271687e-01 -1.337900e-01 -1.882533e-01
#> 
#> $x
#> NULL
#> 
#> $ac
#> [1] 0
#> 
#> $GOF
#> [1] 0.5101729 0.5816490
```

To analyse a distance matrix,

    read_dist_matrix("https://zenodo.org/record/6505843/files/Acts.UBS2.dist.csv") |> do_CMDS()

``` r
library(ANTTV)
## ## read distance matrix, do classical scaling
read_dist_matrix("https://zenodo.org/record/6505843/files/Acts.UBS2.dist.csv") |> do_CMDS()
#> $points
#>                    [,1]         [,2]         [,3]
#> P74        -0.307295481  0.198925004  0.020510499
#> A          -0.283389860  0.232575800  0.025744534
#> B          -0.360204623  0.217764705  0.095651876
#> C          -0.151965418  0.259854026 -0.113457627
#> D          -0.211663578 -0.479404844  0.001452067
#> E           0.045347813  0.052647098  0.137270207
#> P           0.251881508 -0.060674893 -0.015333907
#> Psi         0.068402054  0.026093131  0.083211831
#> 049         0.209268341 -0.060466378 -0.033563366
#> 056         0.229439413 -0.037635066 -0.005653968
#> 0142        0.232886790 -0.027014692 -0.013898920
#> Byz         0.246037527 -0.029849357 -0.048648872
#> Lect        0.290618446  0.027206088 -0.072697656
#> 33         -0.123782841  0.215989387  0.058576134
#> 81         -0.133583186  0.297851380  0.012815394
#> 88          0.166390174  0.059626865 -0.097620945
#> 104         0.165560262  0.010923700 -0.082815788
#> 181        -0.003352919  0.115402653  0.021438824
#> 326         0.163306267  0.025108137  0.045575933
#> 330         0.221280877 -0.064564620 -0.028949856
#> 436         0.146396943  0.027749275  0.013713691
#> 451         0.211991359 -0.082203893 -0.014388511
#> 614         0.117917248 -0.027897723  0.042181925
#> 629         0.078231020  0.036288085 -0.047793923
#> 630         0.081446977  0.149107441  0.008747529
#> 945        -0.004827901  0.156283981 -0.005129556
#> 1241        0.218458828 -0.027919126 -0.021606659
#> 1505        0.174016852  0.021056266 -0.004551897
#> 1739       -0.026403682  0.191324216 -0.016076247
#> 1877        0.209657646 -0.012426281 -0.031947499
#> 2127        0.220476773 -0.041847985 -0.018706080
#> 2412        0.127566597 -0.028884513  0.028294859
#> 2492        0.233107909 -0.026517100  0.031019870
#> 2495        0.179527506  0.009122290 -0.043853538
#> it-ar      -0.237729949 -0.028348937 -0.008447438
#> it-d       -0.297325519 -0.432992515 -0.002835961
#> it-e       -0.022889700 -0.018125398  0.212204707
#> it-gig     -0.220152869 -0.211389026 -0.049032858
#> it-h        0.068829713 -0.213299858  0.035269190
#> it-l       -0.340883005 -0.088534926  0.296763269
#> it-p       -0.102334705 -0.428154931  0.282598745
#> it-r       -0.343996956 -0.038156476 -0.432613818
#> vg         -0.300658729  0.066523724 -0.012370088
#> syr-p      -0.033717162 -0.026640991  0.041680351
#> syr-h       0.048894394 -0.028893643  0.048883607
#> cop-sa     -0.253049715  0.020743395  0.074942869
#> cop-bo     -0.277133682  0.148810951 -0.077077289
#> arm        -0.124476037  0.066431734 -0.092693235
#> eth        -0.152553833 -0.002120714 -0.154816468
#> geo        -0.181188923  0.041223398 -0.012651924
#> Lucifer    -0.075571850 -0.094908952  0.157348359
#> Chrysostom  0.281654632 -0.043478793 -0.077994334
#> Irenaeus   -0.211074396 -0.328474483 -0.337782659
#> Origen     -0.047365900  0.021398419  0.118118026
#> Aleph-c     0.139978550  0.294794965  0.080996591
#> 
#> $eig
#>  [1]  2.170743e+00  1.420023e+00  7.096880e-01  6.344206e-01  5.913380e-01
#>  [6]  5.281594e-01  4.781356e-01  4.429035e-01  3.758280e-01  3.099364e-01
#> [11]  2.680407e-01  2.408380e-01  1.806334e-01  1.649324e-01  1.272414e-01
#> [16]  1.161900e-01  1.051170e-01  9.031685e-02  7.980089e-02  6.683574e-02
#> [21]  6.372648e-02  6.057718e-02  4.882078e-02  4.435976e-02  3.894036e-02
#> [26]  3.361808e-02  2.771772e-02  2.437517e-02  1.879871e-02  1.489760e-02
#> [31]  1.337167e-02  1.241881e-02  8.317663e-03  3.506529e-03  5.512796e-04
#> [36] -2.106063e-16 -2.119653e-03 -3.624185e-03 -3.725051e-03 -6.687740e-03
#> [41] -7.813803e-03 -1.308313e-02 -1.410002e-02 -1.758045e-02 -2.800591e-02
#> [46] -2.907349e-02 -4.310727e-02 -5.052276e-02 -6.640435e-02 -7.867609e-02
#> [51] -1.160947e-01 -1.212386e-01 -1.495245e-01 -3.073556e-01 -8.762284e-01
#> 
#> $x
#> NULL
#> 
#> $ac
#> [1] 0
#> 
#> $GOF
#> [1] 0.3755827 0.4519601
```

Different types of analysis results are obtained by varying the final
step. E.g.

    read_data_frame("https://zenodo.org/record/6466262/files/Mark.UBS4.csv") |> do_reduction() |> do_dist() |> do_NJ()

    read_dist_matrix("https://zenodo.org/record/6505843/files/Acts.UBS2.dist.csv") |> do_NJ()

## Data sets

There are a number of New Testament data sets at the [Zenodo
repository](https://zenodo.org/). (Try searching for *Finney, Tim* to
find them.) Some data sets are data matrices (showing textual states of
witnesses) and others are distance matrices (showing distances between
pairs of witnesses calculated with the simple matching distance). See
the [examples](#examples) above for appropriate command chains.
