# homework 4 - Functions II

## Instructions

1. Use  Aimes housing prices data set from the `/data` folder in this repo. Variable descriptions can be found [here](https://www.kaggle.com/c/house-prices-advanced-regression-techniques/data)

2. Your final document should be an `.md` file (GitHub-flavored markdown) knitted from an R Markdown file. Create a folder called `/homework` where you will add the `.md` file, and a folder called `/src` where you will  place the `.Rmd` file and any other scripts you used to create the reports.

  In answering each of the questions for the assignment please include
  - the question as a header in your R Markdown report,
  - the raw code that you used to generate any tables, and
  - the top ten rows/values/or elements of any resulting tibble, dataframe, vector, or list created in your results.

3. when you are done with your final `push` to this repo, submit the link to this repo on Canvas. (Make sure to `commit` your progress throughout the day, and `push` your progress at the end of each day.)


### Assignment items `[100 pts]`


1. `[20 pts]` __Convert the data to a tibble data-frame.  Use one or more functions from the `purrr` package that subsets list data to subset columns in the data to three unique datasets.  The first should include columns that are factors only (i.e. - categorical data), the second should include columns that are numeric only, and the third should include columns with logical values only.__

  _Hint: Remember that data-frames can be thought of as column-wise lists, so think of each column in your data-frame as a vector in a list that `purrr` functions like `keep()` or `discard()` will subset.  Also not that you can test variable type using functions like `is.numeric()`, `is.factor()`, or `is.character()`)_

2. `[20 pts]` __Using the second dataset from question #1, calculate column means with one of the apply functions.__

3. `[30 pts]`__Using the second dataset from question #1, create a new dataset that only includes the variable indicating sales price (variable name is "SalePrice").__

  __Search for a categorical variable in the full dataset that you think may be related to the sales price of houses.__

  __Use the `split()` function to subset this data into a list containing a single dataset for each category of your data.__

  _Hint: split data into list of datasets by each category using_
   `split(data_with_sales_price,originaldata$categorical_variable)`

  __Create column means for each column of the sales price variable using the `colMeans()` function with one of the map functions on this list.__  

4. `[30 pts]`__Convert the full original housing dataset to a `tibble` and then convert the `tibble` to a list using `as.list()`.__  

  __Subset the list into two unique lists: 1) a new list that includes a single list element that captures the original sales price variable from the Aimes houses data (variable name is "SalePrice").  2) a new list that includes a single list element that captures a variable measuring the building type of each home from the Aimes houses data (variable name is "BldgType").__

  __Lastly, create one more list that appends the the list with building type data to the list with sales price data.__
