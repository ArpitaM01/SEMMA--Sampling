Random Sampling
================
Arpita Majumder
January 4, 2017

R Markdown
----------

This is a R Markdown document for Random sampling methods. Here Smoking dataset is taken from COUNT package to explain the sampling methods. Below is how the dataset looks like :

``` r
# dataset contains only 6 records
head(smoking)
```

    ##   sbp   male smoker age
    ## 1 131   Male     No  34
    ## 2 132   Male     No  36
    ## 3 122   Male     No  30
    ## 4 119 Female     No  32
    ## 5 123 Female     No  26
    ## 6 115 Female     No  23

Summary of the Dataset:

``` r
summary(smoking)
```

    ##       sbp            male              smoker               age       
    ##  Min.   :115.0   Length:6           Length:6           Min.   :23.00  
    ##  1st Qu.:119.8   Class :character   Class :character   1st Qu.:27.00  
    ##  Median :122.5   Mode  :character   Mode  :character   Median :31.00  
    ##  Mean   :123.7                                         Mean   :30.17  
    ##  3rd Qu.:129.0                                         3rd Qu.:33.50  
    ##  Max.   :132.0                                         Max.   :36.00

Say, dataset needs to be divided in Training and Validation dataset. Training contins 70% of the records and Validation contains 30% of the records.

``` r
# sample size is 70% of total rows
Sample_size = floor(0.70 * nrow(smoking))
# set seed to make sampling repeatable
set.seed(1)
# get randomly selected indices for Training dataset
Train_ind = sample(1:nrow(smoking),Sample_size)
```

Training sample set

``` r
Train_sample = smoking[Train_ind, ]
nrow(Train_sample)
```

    ## [1] 4

``` r
summary(Train_sample)
```

    ##       sbp            male              smoker               age       
    ##  Min.   :115.0   Length:4           Length:4           Min.   :23.00  
    ##  1st Qu.:118.0   Class :character   Class :character   1st Qu.:28.25  
    ##  Median :120.5   Mode  :character   Mode  :character   Median :31.00  
    ##  Mean   :122.0                                         Mean   :30.25  
    ##  3rd Qu.:124.5                                         3rd Qu.:33.00  
    ##  Max.   :132.0                                         Max.   :36.00

Validation sample set

``` r
Validation_sample = smoking[-Train_ind, ]
nrow(Validation_sample)
```

    ## [1] 2

``` r
summary(Validation_sample)
```

    ##       sbp          male              smoker               age    
    ##  Min.   :123   Length:2           Length:2           Min.   :26  
    ##  1st Qu.:125   Class :character   Class :character   1st Qu.:28  
    ##  Median :127   Mode  :character   Mode  :character   Median :30  
    ##  Mean   :127                                         Mean   :30  
    ##  3rd Qu.:129                                         3rd Qu.:32  
    ##  Max.   :131                                         Max.   :34
