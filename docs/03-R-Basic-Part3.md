# Data Structures {-}

## Vectors: Creating, indexing, and operations {-}


```r
# Creating a vector
v <- c(1, 2, 3, 4, 5)
print(v)
#> [1] 1 2 3 4 5

# Indexing a vector
print(v[2])  # Access the second element
#> [1] 2

# Vector operations
v2 <- v * 2  # Multiply each element by 2
print(v2)
#> [1]  2  4  6  8 10
```

**Exercise**:

1. Create a vector of your favorite numbers.
2. Access the third element in your vector.
3. Create a new vector that is the square of each element in the original vector.

## Data frames: Creating and exploring data frames {-}


```r
# Creating a data frame
df <- data.frame(
  Name = c("Alice", "Bob", "Charlie"),
  Age = c(25, 30, 35),
  Salary = c(50000, 60000, 70000)
)
print(df)
#>      Name Age Salary
#> 1   Alice  25  50000
#> 2     Bob  30  60000
#> 3 Charlie  35  70000

# Exploring data frames
print(dim(df))  # Dimensions of the data frame
#> [1] 3 3
print(colnames(df))  # Column names
#> [1] "Name"   "Age"    "Salary"
print(summary(df))  # Summary statistics
#>      Name                Age           Salary     
#>  Length:3           Min.   :25.0   Min.   :50000  
#>  Class :character   1st Qu.:27.5   1st Qu.:55000  
#>  Mode  :character   Median :30.0   Median :60000  
#>                     Mean   :30.0   Mean   :60000  
#>                     3rd Qu.:32.5   3rd Qu.:65000  
#>                     Max.   :35.0   Max.   :70000
```

Exercise:

1. Create a data frame with at least three columns and four rows.
1. Print the number of rows and columns of your data frame.
1. Display summary statistics of your data frame.

## Importing and exporting data (CSV files) {-}


```r
# Exporting data to CSV
write.csv(df, "my_data.csv", row.names = FALSE)

# Importing data from CSV
df_imported <- read.csv("my_data.csv")
print(df_imported)
#>      Name Age Salary
#> 1   Alice  25  50000
#> 2     Bob  30  60000
#> 3 Charlie  35  70000
```

