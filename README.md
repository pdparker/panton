
# pantone

<!-- badges: start -->

[![CRAN
status](https://www.r-pkg.org/badges/version/panton)](https://CRAN.R-project.org/package=panton)
[![Lifecycle:
experimental](https://img.shields.io/badge/lifecycle-experimental-orange.svg)](https://www.tidyverse.org/lifecycle/#experimental)
<!-- badges: end -->

The goal of panton is to provide hex values for 1341 Pantone colors
taken from
[https://www.easycalculation.com/colorconverter/pantone-to-hex-table.php](here).

## Installation

You can install the package from [GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("pdparker/pantone")
```

## Example

This is a basic example which shows you how to solve a common problem:

``` r
library(pantone)
data(pantone)

hist(cars$speed, col = pantone[2,2])
```

![](README_files/figure-gfm/example-1.png)<!-- -->

``` r
#install.packages("tidyverse")
library(tidyverse)
rep <- data.frame(y = rep(1:35, 39)[1:1341],
                  x = rep(1:39, each = 35)[1:1341],
                  f = factor(1:1341))
bind_cols(pantone, rep) %>%
  ggplot(aes(x,y, fill = f)) + 
  geom_tile() +
  coord_equal()+
  scale_fill_manual(values = pantone$hex[1:1341]) +
  theme_void() +
  theme(legend.position = "none") +
  labs(title = "All Pantone Colors")
```

![](README_files/figure-gfm/unnamed-chunk-1-1.png)<!-- -->
