Random Sampling
================
Arpita Majumder
January 4, 2017

R Markdown
----------

This is a R Markdown document for Random sampling methods. Here Auto dataset is taken from ISLR package to explain the sampling methods. Below is how the dataset looks like :

``` r
# dataset contains 392 observations
head(Auto)
```

    ##   mpg cylinders displacement horsepower weight acceleration year   origin
    ## 1  18         8          307        130   3504         12.0   70 American
    ## 2  15         8          350        165   3693         11.5   70 American
    ## 3  18         8          318        150   3436         11.0   70 American
    ## 4  16         8          304        150   3433         12.0   70 American
    ## 5  17         8          302        140   3449         10.5   70 American
    ## 6  15         8          429        198   4341         10.0   70 American
    ##                        name
    ## 1 chevrolet chevelle malibu
    ## 2         buick skylark 320
    ## 3        plymouth satellite
    ## 4             amc rebel sst
    ## 5               ford torino
    ## 6          ford galaxie 500

Summary of the Dataset:

``` r
summary(Auto)
```

    ##       mpg        cylinders  displacement     horsepower        weight    
    ##  Min.   : 9.00   3:  4     Min.   : 68.0   Min.   : 46.0   Min.   :1613  
    ##  1st Qu.:17.00   4:199     1st Qu.:105.0   1st Qu.: 75.0   1st Qu.:2225  
    ##  Median :22.75   5:  3     Median :151.0   Median : 93.5   Median :2804  
    ##  Mean   :23.45   6: 83     Mean   :194.4   Mean   :104.5   Mean   :2978  
    ##  3rd Qu.:29.00   8:103     3rd Qu.:275.8   3rd Qu.:126.0   3rd Qu.:3615  
    ##  Max.   :46.60             Max.   :455.0   Max.   :230.0   Max.   :5140  
    ##                                                                          
    ##   acceleration        year        origin                          name    
    ##  Min.   : 8.00   73     : 40   Length:392         amc matador       :  5  
    ##  1st Qu.:13.78   78     : 36   Class :character   ford pinto        :  5  
    ##  Median :15.50   76     : 34   Mode  :character   toyota corolla    :  5  
    ##  Mean   :15.54   75     : 30                      amc gremlin       :  4  
    ##  3rd Qu.:17.02   82     : 30                      amc hornet        :  4  
    ##  Max.   :24.80   70     : 29                      chevrolet chevette:  4  
    ##                  (Other):193                      (Other)           :365

Say, dataset needs to be divided in Training and Validation dataset. Training contins 70% of the records and Validation contains 30% of the records.

``` r
# sample size is 70% of total rows
Sample_size = floor(0.70 * nrow(Auto))
# set seed to make sampling repeatable
set.seed(1)
# get randomly selected indices for Training dataset
Train_ind = sample(1:nrow(Auto),Sample_size)
```

Training sample set

``` r
Train_sample = Auto[Train_ind, ]
nrow(Train_sample)
```

    ## [1] 274

``` r
summary(Train_sample)
```

    ##       mpg        cylinders  displacement     horsepower         weight    
    ##  Min.   : 9.00   3:  2     Min.   : 68.0   Min.   : 46.00   Min.   :1649  
    ##  1st Qu.:17.00   4:138     1st Qu.:105.5   1st Qu.: 76.25   1st Qu.:2239  
    ##  Median :22.35   5:  3     Median :151.0   Median : 93.50   Median :2866  
    ##  Mean   :23.25   6: 58     Mean   :196.4   Mean   :104.84   Mean   :3007  
    ##  3rd Qu.:29.00   8: 73     3rd Qu.:302.0   3rd Qu.:128.00   3rd Qu.:3616  
    ##  Max.   :46.60             Max.   :455.0   Max.   :225.00   Max.   :5140  
    ##                                                                           
    ##   acceleration        year        origin                          name    
    ##  Min.   : 8.50   73     : 29   Length:274         amc matador       :  4  
    ##  1st Qu.:13.82   76     : 25   Class :character   ford maverick     :  4  
    ##  Median :15.50   82     : 24   Mode  :character   ford pinto        :  4  
    ##  Mean   :15.66   75     : 23                      peugeot 504       :  4  
    ##  3rd Qu.:17.27   78     : 23                      chevrolet chevette:  3  
    ##  Max.   :24.80   79     : 23                      chevrolet citation:  3  
    ##                  (Other):127                      (Other)           :252

Validation sample set

``` r
Validation_sample = Auto[-Train_ind, ]
nrow(Validation_sample)
```

    ## [1] 118

``` r
summary(Validation_sample)
```

    ##       mpg        cylinders  displacement     horsepower        weight    
    ##  Min.   :10.00   3: 2      Min.   : 70.0   Min.   : 48.0   Min.   :1613  
    ##  1st Qu.:17.62   4:61      1st Qu.: 98.0   1st Qu.: 75.0   1st Qu.:2220  
    ##  Median :23.00   5: 0      Median :140.0   Median : 93.5   Median :2671  
    ##  Mean   :23.90   6:25      Mean   :189.8   Mean   :103.6   Mean   :2909  
    ##  3rd Qu.:29.75   8:30      3rd Qu.:259.5   3rd Qu.:120.0   3rd Qu.:3612  
    ##  Max.   :44.60             Max.   :454.0   Max.   :230.0   Max.   :4906  
    ##                                                                          
    ##   acceleration        year       origin                        name    
    ##  Min.   : 8.00   70     :13   Length:118         amc gremlin     :  3  
    ##  1st Qu.:13.72   78     :13   Class :character   dodge colt      :  3  
    ##  Median :15.30   73     :11   Mode  :character   honda civic     :  3  
    ##  Mean   :15.28   74     :10                      toyota corolla  :  3  
    ##  3rd Qu.:16.90   80     :10                      amc hornet      :  2  
    ##  Max.   :21.80   71     : 9                      amc matador (sw):  2  
    ##                  (Other):52                      (Other)         :102
