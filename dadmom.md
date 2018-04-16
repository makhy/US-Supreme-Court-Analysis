Tidying `dadmom`
================
Hoi-Ying Mak

Get the data
============

``` r
# don't modify this chunk unless you still need to install rcfss
# if so, run "devtools::install_github("uc-cfss/rcfss")" in the console first

library(tidyverse)
```

    ## ── Attaching packages ────────────────────────────── tidyverse 1.2.1 ──

    ## ✔ ggplot2 2.2.1     ✔ purrr   0.2.4
    ## ✔ tibble  1.4.2     ✔ dplyr   0.7.4
    ## ✔ tidyr   0.8.0     ✔ stringr 1.3.0
    ## ✔ readr   1.1.1     ✔ forcats 0.3.0

    ## ── Conflicts ───────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

``` r
library(rcfss)

data("dadmom")
dadmom
```

    ## # A tibble: 3 x 5
    ##   famid named   incd namem   incm
    ##   <dbl> <chr>  <dbl> <chr>  <dbl>
    ## 1    1. Bill  30000. Bess  15000.
    ## 2    2. Art   22000. Amy   18000.
    ## 3    3. Paul  25000. Pat   50000.

Tidied data
===========

``` r
# Use unite to combine the name and income variables into two categories - dad and mom. Then, mutate and separate the merged cells back into name and income columns.
dadmom %>%
  unite(d, named, incd) %>%
  unite(m, namem, incm) %>%
  gather(d, m, key = gender, value = name_in) %>%
  separate(name_in, into = c("name", "income"))
```

    ## # A tibble: 6 x 4
    ##   famid gender name  income
    ##   <dbl> <chr>  <chr> <chr> 
    ## 1    1. d      Bill  30000 
    ## 2    2. d      Art   22000 
    ## 3    3. d      Paul  25000 
    ## 4    1. m      Bess  15000 
    ## 5    2. m      Amy   18000 
    ## 6    3. m      Pat   50000

Session info
------------

``` r
# don't modify this chunk
devtools::session_info()
```

    ## Session info -------------------------------------------------------------

    ##  setting  value                       
    ##  version  R version 3.4.4 (2018-03-15)
    ##  system   x86_64, darwin15.6.0        
    ##  ui       X11                         
    ##  language (EN)                        
    ##  collate  en_US.UTF-8                 
    ##  tz       America/Chicago             
    ##  date     2018-04-15

    ## Packages -----------------------------------------------------------------

    ##  package    * version   date       source                           
    ##  assertthat   0.2.0     2017-04-11 CRAN (R 3.4.0)                   
    ##  backports    1.1.2     2017-12-13 cran (@1.1.2)                    
    ##  base       * 3.4.4     2018-03-15 local                            
    ##  bindr        0.1.1     2018-03-13 CRAN (R 3.4.4)                   
    ##  bindrcpp     0.2       2017-06-17 CRAN (R 3.4.0)                   
    ##  broom        0.4.3     2017-11-20 CRAN (R 3.4.3)                   
    ##  cellranger   1.1.0     2016-07-27 cran (@1.1.0)                    
    ##  cli          1.0.0     2017-11-05 CRAN (R 3.4.2)                   
    ##  colorspace   1.3-2     2016-12-14 cran (@1.3-2)                    
    ##  compiler     3.4.4     2018-03-15 local                            
    ##  crayon       1.3.4     2017-09-16 CRAN (R 3.4.1)                   
    ##  datasets   * 3.4.4     2018-03-15 local                            
    ##  devtools     1.13.5    2018-02-18 CRAN (R 3.4.3)                   
    ##  digest       0.6.15    2018-01-28 CRAN (R 3.4.3)                   
    ##  dplyr      * 0.7.4     2017-09-28 CRAN (R 3.4.2)                   
    ##  evaluate     0.10.1    2017-06-24 cran (@0.10.1)                   
    ##  forcats    * 0.3.0     2018-02-19 cran (@0.3.0)                    
    ##  foreign      0.8-69    2017-06-22 CRAN (R 3.4.4)                   
    ##  ggplot2    * 2.2.1     2016-12-30 cran (@2.2.1)                    
    ##  glue         1.2.0     2017-10-29 CRAN (R 3.4.2)                   
    ##  graphics   * 3.4.4     2018-03-15 local                            
    ##  grDevices  * 3.4.4     2018-03-15 local                            
    ##  grid         3.4.4     2018-03-15 local                            
    ##  gtable       0.2.0     2016-02-26 cran (@0.2.0)                    
    ##  haven        1.1.1     2018-01-18 cran (@1.1.1)                    
    ##  hms          0.4.2     2018-03-10 cran (@0.4.2)                    
    ##  htmltools    0.3.6     2017-04-28 cran (@0.3.6)                    
    ##  httr         1.3.1     2017-08-20 CRAN (R 3.4.1)                   
    ##  jsonlite     1.5       2017-06-01 CRAN (R 3.4.0)                   
    ##  knitr        1.20      2018-02-20 CRAN (R 3.4.3)                   
    ##  lattice      0.20-35   2017-03-25 CRAN (R 3.4.4)                   
    ##  lazyeval     0.2.1     2017-10-29 cran (@0.2.1)                    
    ##  lubridate    1.7.3     2018-02-27 cran (@1.7.3)                    
    ##  magrittr     1.5       2014-11-22 CRAN (R 3.4.0)                   
    ##  memoise      1.1.0     2017-04-21 CRAN (R 3.4.0)                   
    ##  methods    * 3.4.4     2018-03-15 local                            
    ##  mnormt       1.5-5     2016-10-15 CRAN (R 3.4.0)                   
    ##  modelr       0.1.1     2017-07-24 cran (@0.1.1)                    
    ##  munsell      0.4.3     2016-02-13 cran (@0.4.3)                    
    ##  nlme         3.1-131.1 2018-02-16 CRAN (R 3.4.4)                   
    ##  parallel     3.4.4     2018-03-15 local                            
    ##  pillar       1.2.1     2018-02-27 CRAN (R 3.4.3)                   
    ##  pkgconfig    2.0.1     2017-03-21 CRAN (R 3.4.0)                   
    ##  plyr         1.8.4     2016-06-08 CRAN (R 3.4.0)                   
    ##  psych        1.7.8     2017-09-09 CRAN (R 3.4.4)                   
    ##  purrr      * 0.2.4     2017-10-18 CRAN (R 3.4.2)                   
    ##  R6           2.2.2     2017-06-17 CRAN (R 3.4.0)                   
    ##  rcfss      * 0.1.5     2018-04-04 Github (uc-cfss/rcfss@8d2b2c0)   
    ##  Rcpp         0.12.16   2018-03-13 CRAN (R 3.4.4)                   
    ##  readr      * 1.1.1     2017-05-16 cran (@1.1.1)                    
    ##  readxl       1.0.0     2017-04-18 cran (@1.0.0)                    
    ##  reshape2     1.4.3     2017-12-11 CRAN (R 3.4.3)                   
    ##  rlang        0.2.0     2018-02-20 CRAN (R 3.4.3)                   
    ##  rmarkdown    1.9       2018-03-01 CRAN (R 3.4.3)                   
    ##  rprojroot    1.3-2     2018-01-03 cran (@1.3-2)                    
    ##  rstudioapi   0.7       2017-09-07 CRAN (R 3.4.1)                   
    ##  rvest        0.3.2     2016-06-17 cran (@0.3.2)                    
    ##  scales       0.5.0     2017-08-24 cran (@0.5.0)                    
    ##  stats      * 3.4.4     2018-03-15 local                            
    ##  stringi      1.1.7     2018-03-12 CRAN (R 3.4.4)                   
    ##  stringr    * 1.3.0     2018-02-19 CRAN (R 3.4.3)                   
    ##  tibble     * 1.4.2     2018-01-22 CRAN (R 3.4.3)                   
    ##  tidyr      * 0.8.0     2018-01-29 CRAN (R 3.4.3)                   
    ##  tidyselect   0.2.4     2018-02-26 CRAN (R 3.4.3)                   
    ##  tidyverse  * 1.2.1     2018-03-30 Github (hadley/tidyverse@03ccf9c)
    ##  tools        3.4.4     2018-03-15 local                            
    ##  utf8         1.1.3     2018-01-03 CRAN (R 3.4.3)                   
    ##  utils      * 3.4.4     2018-03-15 local                            
    ##  withr        2.1.2     2018-03-15 CRAN (R 3.4.4)                   
    ##  xml2         1.2.0     2018-01-24 cran (@1.2.0)                    
    ##  yaml         2.1.18    2018-03-08 cran (@2.1.18)
