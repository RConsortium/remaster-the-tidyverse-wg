Data Wrangling with the Tidyverse
================
10/21/2024

## Presentation 1

Presentation 1 does not contain data examples.

## Exercise + Presentation 2

### band + instrument data

band, instrument and instrument2 datasets are created in the exercise to
practice joins.

``` r
band <- tribble(
   ~name,     ~band,
  "Mick",  "Stones",
  "John", "Beatles",
  "Paul", "Beatles"
)

instrument <- tribble(
    ~name,   ~plays,
   "John", "guitar",
   "Paul",   "bass",
  "Keith", "guitar"
)

instrument2 <- tribble(
    ~artist,   ~plays,
   "John", "guitar",
   "Paul",   "bass",
  "Keith", "guitar"
)
```

### flights + airlines data

Flights and airlines datasets are joined together to answer questions
using both data sets.

``` r
datasize(flights)
```

    ## Number of Columns: 19
    ## Number of Rows: 336776

``` r
flights %>% head()
```

    ## # A tibble: 6 x 19
    ##    year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##   <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ## 1  2013     1     1      517            515         2      830            819
    ## 2  2013     1     1      533            529         4      850            830
    ## 3  2013     1     1      542            540         2      923            850
    ## 4  2013     1     1      544            545        -1     1004           1022
    ## 5  2013     1     1      554            600        -6      812            837
    ## 6  2013     1     1      554            558        -4      740            728
    ## # ... with 11 more variables: arr_delay <dbl>, carrier <chr>, flight <int>,
    ## #   tailnum <chr>, origin <chr>, dest <chr>, air_time <dbl>, distance <dbl>,
    ## #   hour <dbl>, minute <dbl>, time_hour <dttm>

``` r
flights %>% sapply(class)
```

    ## $year
    ## [1] "integer"
    ## 
    ## $month
    ## [1] "integer"
    ## 
    ## $day
    ## [1] "integer"
    ## 
    ## $dep_time
    ## [1] "integer"
    ## 
    ## $sched_dep_time
    ## [1] "integer"
    ## 
    ## $dep_delay
    ## [1] "numeric"
    ## 
    ## $arr_time
    ## [1] "integer"
    ## 
    ## $sched_arr_time
    ## [1] "integer"
    ## 
    ## $arr_delay
    ## [1] "numeric"
    ## 
    ## $carrier
    ## [1] "character"
    ## 
    ## $flight
    ## [1] "integer"
    ## 
    ## $tailnum
    ## [1] "character"
    ## 
    ## $origin
    ## [1] "character"
    ## 
    ## $dest
    ## [1] "character"
    ## 
    ## $air_time
    ## [1] "numeric"
    ## 
    ## $distance
    ## [1] "numeric"
    ## 
    ## $hour
    ## [1] "numeric"
    ## 
    ## $minute
    ## [1] "numeric"
    ## 
    ## $time_hour
    ## [1] "POSIXct" "POSIXt"

``` r
datasize(airlines)
```

    ## Number of Columns: 2
    ## Number of Rows: 16

``` r
airlines %>% head()
```

    ## # A tibble: 6 x 2
    ##   carrier name                    
    ##   <chr>   <chr>                   
    ## 1 9E      Endeavor Air Inc.       
    ## 2 AA      American Airlines Inc.  
    ## 3 AS      Alaska Airlines Inc.    
    ## 4 B6      JetBlue Airways         
    ## 5 DL      Delta Air Lines Inc.    
    ## 6 EV      ExpressJet Airlines Inc.

``` r
airlines %>% sapply(class)
```

    ##     carrier        name 
    ## "character" "character"

### Your Turn Example

Below is an example exercise using the flights and airlines. The blanks
need to be filled in to join airlines and flights data and find the
largest arrival delays by airline. Other exercises include finding the
average delay and number of airports serviced.

``` r
flights %>%
  filter(!is.na(arr_delay)) %>%
  __________________  %>%
  group_by(_________) %>%
  __________________  %>%
  arrange(__________) 
```

## Exercise + Presentation 3

### flights data

flights data from exercise 2 is used again to summarize delayed flights.

### Your Turn Example

The exercise asks to create a summary table that shows:

1.  How many flights were delayed  
2.  What proportion of flights were delayed

### babynames data

babynames data is used again to calculate the weighted mean of last
letter in name by age and sex.

### Your Turn Example

Below is the code that needs to be filled in to calculate the weighted
mean of last letter in name by age and sex.

``` r
babynames %>%
  _______(last = _________, 
          vowel = __________) %>%
  group_by(__________) %>%
  _________(p_vowel = weighted.mean(vowel, n)) %>%
  _________ +
  __________
```

### gss\_cat data

gss\_cat data is used to look at the relationship between TV consumption
and other demographic variables.

``` r
datasize(gss_cat)
```

    ## Number of Columns: 9
    ## Number of Rows: 21483

``` r
gss_cat %>% head()
```

    ## # A tibble: 6 x 9
    ##    year marital         age race  rincome        partyid     relig denom tvhours
    ##   <int> <fct>         <int> <fct> <fct>          <fct>       <fct> <fct>   <int>
    ## 1  2000 Never married    26 White $8000 to 9999  Ind,near r~ Prot~ Sout~      12
    ## 2  2000 Divorced         48 White $8000 to 9999  Not str re~ Prot~ Bapt~      NA
    ## 3  2000 Widowed          67 White Not applicable Independent Prot~ No d~       2
    ## 4  2000 Never married    39 White Not applicable Ind,near r~ Orth~ Not ~       4
    ## 5  2000 Divorced         25 White Not applicable Not str de~ None  Not ~       1
    ## 6  2000 Married          25 White $20000 - 24999 Strong dem~ Prot~ Sout~      NA

``` r
gss_cat %>% sapply(class)
```

    ##      year   marital       age      race   rincome   partyid     relig     denom 
    ## "integer"  "factor" "integer"  "factor"  "factor"  "factor"  "factor"  "factor" 
    ##   tvhours 
    ## "integer"

### Your Turn Example

Below is an example of an exercise to a graph of create average TV
consumption by marital status.

``` r
gss_cat <- gss_cat %>%
  filter(_is.na(________)) %>%
  group_by(________) %>%
  summarise(_________________) %>%
  ggplot() +
    geom_point(mapping = aes(x = _______, y = _________________________))
```

## Exercise + Presentation 4

### pollution + cases data

pollution and cases data are created within the exercise for practice
with `gather()` and `spread()` functions.

``` r
cases <- tribble(
  ~Country, ~"2011", ~"2012", ~"2013",
      "FR",    7000,    6900,    7000,
      "DE",    5800,    6000,    6200,
      "US",   15000,   14000,   13000
)

pollution <- tribble(
       ~city, ~size, ~amount,
  "New York", "large",      23,
  "New York", "small",      14,
    "London", "large",      22,
    "London", "small",      16,
   "Beijing", "large",     121,
   "Beijing", "small",     121
)
```

### who data

who data is reshaped using `gather()`

``` r
datasize(who)
```

    ## Number of Columns: 60
    ## Number of Rows: 7240

``` r
who %>% head()
```

    ## # A tibble: 6 x 60
    ##   country   iso2  iso3   year new_sp_m014 new_sp_m1524 new_sp_m2534 new_sp_m3544
    ##   <chr>     <chr> <chr> <int>       <int>        <int>        <int>        <int>
    ## 1 Afghanis~ AF    AFG    1980          NA           NA           NA           NA
    ## 2 Afghanis~ AF    AFG    1981          NA           NA           NA           NA
    ## 3 Afghanis~ AF    AFG    1982          NA           NA           NA           NA
    ## 4 Afghanis~ AF    AFG    1983          NA           NA           NA           NA
    ## 5 Afghanis~ AF    AFG    1984          NA           NA           NA           NA
    ## 6 Afghanis~ AF    AFG    1985          NA           NA           NA           NA
    ## # ... with 52 more variables: new_sp_m4554 <int>, new_sp_m5564 <int>,
    ## #   new_sp_m65 <int>, new_sp_f014 <int>, new_sp_f1524 <int>,
    ## #   new_sp_f2534 <int>, new_sp_f3544 <int>, new_sp_f4554 <int>,
    ## #   new_sp_f5564 <int>, new_sp_f65 <int>, new_sn_m014 <int>,
    ## #   new_sn_m1524 <int>, new_sn_m2534 <int>, new_sn_m3544 <int>,
    ## #   new_sn_m4554 <int>, new_sn_m5564 <int>, new_sn_m65 <int>,
    ## #   new_sn_f014 <int>, new_sn_f1524 <int>, new_sn_f2534 <int>, ...

``` r
who %>% sapply(class)
```

    ##      country         iso2         iso3         year  new_sp_m014 new_sp_m1524 
    ##  "character"  "character"  "character"    "integer"    "integer"    "integer" 
    ## new_sp_m2534 new_sp_m3544 new_sp_m4554 new_sp_m5564   new_sp_m65  new_sp_f014 
    ##    "integer"    "integer"    "integer"    "integer"    "integer"    "integer" 
    ## new_sp_f1524 new_sp_f2534 new_sp_f3544 new_sp_f4554 new_sp_f5564   new_sp_f65 
    ##    "integer"    "integer"    "integer"    "integer"    "integer"    "integer" 
    ##  new_sn_m014 new_sn_m1524 new_sn_m2534 new_sn_m3544 new_sn_m4554 new_sn_m5564 
    ##    "integer"    "integer"    "integer"    "integer"    "integer"    "integer" 
    ##   new_sn_m65  new_sn_f014 new_sn_f1524 new_sn_f2534 new_sn_f3544 new_sn_f4554 
    ##    "integer"    "integer"    "integer"    "integer"    "integer"    "integer" 
    ## new_sn_f5564   new_sn_f65  new_ep_m014 new_ep_m1524 new_ep_m2534 new_ep_m3544 
    ##    "integer"    "integer"    "integer"    "integer"    "integer"    "integer" 
    ## new_ep_m4554 new_ep_m5564   new_ep_m65  new_ep_f014 new_ep_f1524 new_ep_f2534 
    ##    "integer"    "integer"    "integer"    "integer"    "integer"    "integer" 
    ## new_ep_f3544 new_ep_f4554 new_ep_f5564   new_ep_f65  newrel_m014 newrel_m1524 
    ##    "integer"    "integer"    "integer"    "integer"    "integer"    "integer" 
    ## newrel_m2534 newrel_m3544 newrel_m4554 newrel_m5564   newrel_m65  newrel_f014 
    ##    "integer"    "integer"    "integer"    "integer"    "integer"    "integer" 
    ## newrel_f1524 newrel_f2534 newrel_f3544 newrel_f4554 newrel_f5564   newrel_f65 
    ##    "integer"    "integer"    "integer"    "integer"    "integer"    "integer"

### Your Turn Example

Using the who data the blank need to be filled in to separate the
`sexage` column into `sex` and `age` columns.

``` r
who %>%
  gather("codes", "n", 5:60) %>%
  select(-iso2, -iso3) %>%
  separate(codes, c("new", "type", "sexage"), sep = "_") %>%
  select(-new) %>% 
  _______________________________
```

### babynames data

babynames data is used again and reshaped to show male and female
proportion of children by year.

### Your Turn Example

In the exercise the below data set needs to be reshaped that Male and
Females are columns. Then a plot is created from the data.

``` r
babynames %>%
group_by(year, sex) %>%
summarise(n = sum(n)) %>%
  head()
```

    ## # A tibble: 6 x 3
    ## # Groups:   year [3]
    ##    year sex        n
    ##   <dbl> <chr>  <int>
    ## 1  1880 F      90993
    ## 2  1880 M     110491
    ## 3  1881 F      91953
    ## 4  1881 M     100743
    ## 5  1882 F     107847
    ## 6  1882 M     113686

## Exercise + Presentation 5

### exams lists

exams is a list of student test scores used to compute average score per
student.

``` r
set.seed(1000)
exams <- list(
  student1 = round(runif(10, 50, 100)),
  student2 = round(runif(10, 50, 100)),
  student3 = round(runif(10, 50, 100)),
  student4 = round(runif(10, 50, 100)),
  student5 = round(runif(10, 50, 100))
)

extra_credit <- list(0, 0, 10, 10, 15)

exams
```

    ## $student1
    ##  [1] 66 88 56 85 76 53 87 79 61 63
    ## 
    ## $student2
    ##  [1] 67 88 66 93 88 54 75 82 54 79
    ## 
    ## $student3
    ##  [1] 58 90 64 54 77 84 73 91 55 56
    ## 
    ## $student4
    ##  [1] 78 52 78 98 75 85 51 89 79 66
    ## 
    ## $student5
    ##  [1] 100  77  55  82  90  86  85  78  63  75

### who data

who data from exercise 4 is used again to create a linear model
predicting TB cases in 2020 by country.

### sw\_people list

sw\_people is a list of star wars characters and attributes. It is used
to answer if Anakin Skywalker or Darth Vader is taller.
