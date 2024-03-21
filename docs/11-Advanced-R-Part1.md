
# Part I: Advanced Data Manipulation with dplyr (30 minutes) {-}
## Grouping and summarizing data {-}


```r
# Loading the dplyr package
library(dplyr)
#> 
#> Attaching package: 'dplyr'
#> The following objects are masked from 'package:stats':
#> 
#>     filter, lag
#> The following objects are masked from 'package:base':
#> 
#>     intersect, setdiff, setequal, union

# Using the 'mtcars' dataset
data(mtcars)

# Example: Grouping by 'cyl' (number of cylinders) and calculating mean mpg (miles per gallon)
grouped_data <- mtcars %>%
  group_by(cyl) %>%
  summarize(mean_mpg = mean(mpg))
print(grouped_data)
#> # A tibble: 3 × 2
#>     cyl mean_mpg
#>   <dbl>    <dbl>
#> 1     4     26.7
#> 2     6     19.7
#> 3     8     15.1
```
*Exercise*: 

1. Group the 'mtcars' dataset by 'gear' and calculate the average horsepower ('hp') for each gear group.


## Joining and merging datasets {-}


```r
# Creating a sample dataset to join with 'mtcars'
car_names <- data.frame(model = rownames(mtcars), car_type = rep(c("Type A", "Type B", "Type C"), length.out = nrow(mtcars)))

# Converting row names of 'mtcars' to a column
mtcars$model <- rownames(mtcars)

# Example: Joining 'mtcars' and 'car_names'
joined_data <- left_join(mtcars, car_names, by = "model")
print(head(joined_data))
#>    mpg cyl disp  hp drat    wt  qsec vs am gear carb
#> 1 21.0   6  160 110 3.90 2.620 16.46  0  1    4    4
#> 2 21.0   6  160 110 3.90 2.875 17.02  0  1    4    4
#> 3 22.8   4  108  93 3.85 2.320 18.61  1  1    4    1
#> 4 21.4   6  258 110 3.08 3.215 19.44  1  0    3    1
#> 5 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2
#> 6 18.1   6  225 105 2.76 3.460 20.22  1  0    3    1
#>               model car_type
#> 1         Mazda RX4   Type A
#> 2     Mazda RX4 Wag   Type B
#> 3        Datsun 710   Type C
#> 4    Hornet 4 Drive   Type A
#> 5 Hornet Sportabout   Type B
#> 6           Valiant   Type C
```

*Exercise:*

2. Create a new dataframe with a subset of columns from 'iris' and merge it with the original 'iris' dataset based on a common column.
