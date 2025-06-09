Welcome to the Tidyverse
================
10/21/2024

## Exercise + Presentation 1

### Cars data

From cars data, `speed` and `dist` and are used to create a scatter
plot.

``` r
datasize(cars)
```

    ## Number of Columns: 2
    ## Number of Rows: 50

``` r
head(cars)
```

    ##   speed dist
    ## 1     4    2
    ## 2     4   10
    ## 3     7    4
    ## 4     7   22
    ## 5     8   16
    ## 6     9   10

``` r
sapply(cars, class)
```

    ##     speed      dist 
    ## "numeric" "numeric"

## Exercise + Presentation 2

### mpg data

mpg data is used to create plots such as a scatter plot with `displ` on
the x-axis and `hwy` on the y-axis. Out of the 11 variables only 5 are
used in the exercise.

``` r
datasize(mpg)
```

    ## Number of Columns: 11
    ## Number of Rows: 234

``` r
mpg %>% select(displ, hwy, class, drv, cyl) %>% head()
```

    ## # A tibble: 6 x 5
    ##   displ   hwy class   drv     cyl
    ##   <dbl> <int> <chr>   <chr> <int>
    ## 1   1.8    29 compact f         4
    ## 2   1.8    29 compact f         4
    ## 3   2      31 compact f         4
    ## 4   2      30 compact f         4
    ## 5   2.8    26 compact f         6
    ## 6   2.8    26 compact f         6

``` r
mpg %>% select(displ, hwy, class, drv, cyl) %>% sapply(class)
```

    ##       displ         hwy       class         drv         cyl 
    ##   "numeric"   "integer" "character" "character"   "integer"

#### Your Turn Example

Below is an example of the scatter plot created in a presentaion
example. Further examples modify the plot by adding coloring and facet
wrapping. Additionally, histograms and boxplots are created using `hwy`.

``` r
ggplot(data = mpg) +
 geom_point(mapping = aes(x = displ, y = hwy))
```

![](tidyverse_data_catalogue_files/figure-gfm/unnamed-chunk-8-1.png)<!-- -->

## Exercise + Presentation 3

### babynames data

babynames is used to practice transforming data through methods such as
filtering and boolean operations.

``` r
datasize(babynames)
```

    ## Number of Columns: 5
    ## Number of Rows: 1924665

``` r
head(babynames)
```

    ## # A tibble: 6 x 5
    ##    year sex   name          n   prop
    ##   <dbl> <chr> <chr>     <int>  <dbl>
    ## 1  1880 F     Mary       7065 0.0724
    ## 2  1880 F     Anna       2604 0.0267
    ## 3  1880 F     Emma       2003 0.0205
    ## 4  1880 F     Elizabeth  1939 0.0199
    ## 5  1880 F     Minnie     1746 0.0179
    ## 6  1880 F     Margaret   1578 0.0162

``` r
babynames %>% sapply(class)
```

    ##        year         sex        name           n        prop 
    ##   "numeric" "character" "character"   "integer"   "numeric"

#### Your Turn Example

In the presentation babynames is used for boolean operations such as the
example below. It is also used for other cases such as finding the most
popular girls names in 2017, plotting name proportion over time and
finding the earliest appearance of names.

``` r
filter(babynames, name == "Sea" | name ==
"Anemone")
```

    ## # A tibble: 5 x 5
    ##    year sex   name        n       prop
    ##   <dbl> <chr> <chr>   <int>      <dbl>
    ## 1  1982 F     Sea         5 0.00000276
    ## 2  1985 M     Sea         6 0.00000312
    ## 3  1986 M     Sea         5 0.0000026 
    ## 4  1998 F     Sea         5 0.00000258
    ## 5  2012 F     Anemone     6 0.0000031

## Exercise + Presentation 4

### wages data

wages data is used to create models with `income` as the dependent
variable.

``` r
datasize(wages)
```

    ## Number of Columns: 8
    ## Number of Rows: 5266

``` r
head(wages)
```

    ## # A tibble: 6 x 8
    ##   income height weight   age marital  sex    education afqt  
    ##    <dbl>  <dbl> <chr>  <dbl> <chr>    <chr>  <chr>     <chr> 
    ## 1  19000     60 155.0     53 married  female 13.0      6.841 
    ## 2  35000     70 156.0     51 married  female 10.0      49.444
    ## 3 105000     65 195.0     52 married  male   16.0      99.393
    ## 4  40000     63 197.0     54 married  female 14.0      44.022
    ## 5  75000     66 190.0     49 married  male   14.0      59.683
    ## 6 102000     68 200.0     49 divorced female 18.0      98.798

``` r
wages %>% sapply(class)
```

    ##      income      height      weight         age     marital         sex 
    ##   "numeric"   "numeric" "character"   "numeric" "character" "character" 
    ##   education        afqt 
    ## "character" "character"

### Your Turn Example

Below is an example of the linear model created and displayed in a graph
from the presentation. The model is also used with different independent
variables such as `height` and `sex`. The model is later used for
predictions.

``` r
wages %>%
ggplot(aes(x = height, y = log(income))) +
geom_point(alpha = 0.1) + 
geom_smooth(method = lm)
```

![](tidyverse_data_catalogue_files/figure-gfm/unnamed-chunk-17-1.png)<!-- -->

## Exercise + Presentation 5

### babynames data

babynames from exercise 3 is used again to create a dashboard with a
plot showing the proportion of names by gender over time.

### Your Turn example

The exercises in this presentation are related to R Markdown rather than
the data.
