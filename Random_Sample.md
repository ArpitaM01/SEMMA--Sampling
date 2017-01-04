Random Sampling
================
Arpita Majumder
January 4, 2017

R Markdown
----------

This is a R Markdown document for Random sampling methods. Here Smoking dataset is taken from COUNT package to explain the sampling methods. Below is how the dataset looks like :

``` r
head(smoking)
```

    ##   sbp male smoker age
    ## 1 131    1      1  34
    ## 2 132    1      1  36
    ## 3 122    1      0  30
    ## 4 119    0      0  32
    ## 5 123    0      1  26
    ## 6 115    0      0  23

Summary of the Dataset:

``` r
summary(smoking)
```

    ##       sbp             male         smoker         age       
    ##  Min.   :115.0   Min.   :0.0   Min.   :0.0   Min.   :23.00  
    ##  1st Qu.:119.8   1st Qu.:0.0   1st Qu.:0.0   1st Qu.:27.00  
    ##  Median :122.5   Median :0.5   Median :0.5   Median :31.00  
    ##  Mean   :123.7   Mean   :0.5   Mean   :0.5   Mean   :30.17  
    ##  3rd Qu.:129.0   3rd Qu.:1.0   3rd Qu.:1.0   3rd Qu.:33.50  
    ##  Max.   :132.0   Max.   :1.0   Max.   :1.0   Max.   :36.00
