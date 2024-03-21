# Part IV: Data Manipulation (30 minutes) {-}

## Subsetting and filtering data {-}


```r
# Creating a sample data frame
data <- data.frame(
  id = 1:5,
  name = c("Alice", "Bob", "Charlie", "David", "Eva"),
  age = c(25, 30, 22, 28, 24)
)
# Subsetting by a specific column
ages <- data$age
print(ages)
#> [1] 25 30 22 28 24

# Filtering data based on a condition
young_adults <- subset(data, age < 30)
print(young_adults)
#>   id    name age
#> 1  1   Alice  25
#> 3  3 Charlie  22
#> 4  4   David  28
#> 5  5     Eva  24
```

## Adding, removing, and renaming columns {-}


```r
# Adding a new column 'salary'
data$salary <- c(55000, 50000, 60000, 52000, 58000)
print(data)
#>   id    name age salary
#> 1  1   Alice  25  55000
#> 2  2     Bob  30  50000
#> 3  3 Charlie  22  60000
#> 4  4   David  28  52000
#> 5  5     Eva  24  58000

# Removing the 'salary' column
data$salary <- NULL
print(data)
#>   id    name age
#> 1  1   Alice  25
#> 2  2     Bob  30
#> 3  3 Charlie  22
#> 4  4   David  28
#> 5  5     Eva  24

# Renaming the 'name' column to 'first_name'
names(data)[names(data) == "name"] <- "first_name"
print(data)
#>   id first_name age
#> 1  1      Alice  25
#> 2  2        Bob  30
#> 3  3    Charlie  22
#> 4  4      David  28
#> 5  5        Eva  24
```

## Basic data summary and exploration {-}


```r
# Summary statistics of the data frame
summary(data)
#>        id     first_name             age      
#>  Min.   :1   Length:5           Min.   :22.0  
#>  1st Qu.:2   Class :character   1st Qu.:24.0  
#>  Median :3   Mode  :character   Median :25.0  
#>  Mean   :3                      Mean   :25.8  
#>  3rd Qu.:4                      3rd Qu.:28.0  
#>  Max.   :5                      Max.   :30.0

# Structure of the data frame
str(data)
#> 'data.frame':	5 obs. of  3 variables:
#>  $ id        : int  1 2 3 4 5
#>  $ first_name: chr  "Alice" "Bob" "Charlie" "David" ...
#>  $ age       : num  25 30 22 28 24

# Average age of the individuals in the data frame
average_age <- mean(data$age)
print(average_age)
#> [1] 25.8

# Count of unique names in the data frame
unique_names_count <- length(unique(data$first_name))
print(unique_names_count)
#> [1] 5
```

