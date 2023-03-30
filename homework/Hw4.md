-   [Homework 4 - Functions II](#homework-4---functions-ii)
    -   [loading dataset](#loading-dataset)
    -   [Convert the data to a tibble data-frame. Use one or more
        functions from the purrr package that subsets list data to
        subset columns in the data to three unique datasets. The first
        should include columns that are factors only (i.e. - categorical
        data), the second should include columns that are numeric only,
        and the third should include columns with logical values
        only.](#convert-the-data-to-a-tibble-data-frame.-use-one-or-more-functions-from-the-purrr-package-that-subsets-list-data-to-subset-columns-in-the-data-to-three-unique-datasets.-the-first-should-include-columns-that-are-factors-only-i.e.---categorical-data-the-second-should-include-columns-that-are-numeric-only-and-the-third-should-include-columns-with-logical-values-only.)
    -   [Using the second dataset from question #1, calculate column
        means with one of the apply
        functions.](#using-the-second-dataset-from-question-1-calculate-column-means-with-one-of-the-apply-functions.)
    -   [Using the numeric_only dataset to create a new dataset that
        only includes the variable indicating sales price (variable name
        is
        “SalePrice”).](#using-the-numeric_only-dataset-to-create-a-new-dataset-that-only-includes-the-variable-indicating-sales-price-variable-name-is-saleprice.)
    -   [Convert the full original housing dataset to a tibble and then
        convert the tibble to a list using
        as.list().](#convert-the-full-original-housing-dataset-to-a-tibble-and-then-convert-the-tibble-to-a-list-using-as.list.)

# Homework 4 - Functions II

## loading dataset

``` r
library(tidyverse)
```

    ## -- Attaching packages --------------------------------------- tidyverse 1.3.1 --

    ## v ggplot2 3.3.5     v purrr   0.3.4
    ## v tibble  3.1.2     v dplyr   1.0.7
    ## v tidyr   1.1.3     v stringr 1.4.0
    ## v readr   1.4.0     v forcats 0.5.1

    ## -- Conflicts ------------------------------------------ tidyverse_conflicts() --
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

``` r
library(readr)
library(purrr)
```

## Convert the data to a tibble data-frame. Use one or more functions from the purrr package that subsets list data to subset columns in the data to three unique datasets. The first should include columns that are factors only (i.e. - categorical data), the second should include columns that are numeric only, and the third should include columns with logical values only.

``` r
my_data <- read.table(file='Housing_prices_data.csv', header=TRUE, sep=",");

my_tibble <- as_tibble(my_data)

factors_only <- my_tibble %>% keep(is.factor)

numeric_only <- my_tibble %>% keep(is.numeric)

logical_only <- my_tibble %>% keep(is.logical)
```

## Using the second dataset from question #1, calculate column means with one of the apply functions.

``` r
col_means <- apply(numeric_only, 2, mean)
```

## Using the numeric_only dataset to create a new dataset that only includes the variable indicating sales price (variable name is “SalePrice”).

``` r
sales_price <- numeric_only %>% select(SalePrice)
my_data_split <- split(sales_price, my_data$BldgType)
col_means <- map_dbl(my_data_split, colMeans)
```

## Convert the full original housing dataset to a tibble and then convert the tibble to a list using as.list().

``` r
data_tibble <- as_tibble(my_data)
data_list <- as.list(data_tibble)
sales_price_list <- list(data_list$SalePrice)
bldg_type_list <- list(data_list$BldgType)
```
