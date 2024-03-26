
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

You can give names to the columns of the vector 

```r
my_vector <- c("Katrien Antonio", "teacher")
names(my_vector) <- c("Name", "Profession")
my_vector
#>              Name        Profession 
#> "Katrien Antonio"         "teacher"
```

**Exercise**:

1. Create a vector of your favorite numbers.
2. Access the third element in your vector.
3. Create a new vector that is the square of each element in the original vector.

## Matrices {-}

Matrices are vectors with a dimension attribute. The dimension attribute is itself an integer vector of length 2 (number of rows, number of columns)

Matrices are constructed column-wise, so entries can be thought of starting in the “upper left” corner and running down the columns.


```r
m <- matrix(1:6, nrow = 2, ncol = 3) 
m
#>      [,1] [,2] [,3]
#> [1,]    1    3    5
#> [2,]    2    4    6
```

Another example

```r
my_matrix <- matrix(1:12, 3, 4, byrow = TRUE)
my_matrix
#>      [,1] [,2] [,3] [,4]
#> [1,]    1    2    3    4
#> [2,]    5    6    7    8
#> [3,]    9   10   11   12
```

Matrices can be created by column-binding or row-binding with the `cbind()` and `rbind()` functions.


```r
x <- 1:3
y <- 10:12
cbind(x, y)
#>      x  y
#> [1,] 1 10
#> [2,] 2 11
#> [3,] 3 12
rbind(x, y)
#>   [,1] [,2] [,3]
#> x    1    2    3
#> y   10   11   12
```

## Lists {-}

Lists are a special type of vector that can contain elements of different classes. Lists are a very important data type in R and you should get to know them well. Lists, in combination with the various “apply” functions discussed later, make for a powerful combination.

Lists can be explicitly created using the list() function, which takes an arbitrary number of arguments.


```r
x <- list(1, "a", TRUE, 1 + 4i) 
x
#> [[1]]
#> [1] 1
#> 
#> [[2]]
#> [1] "a"
#> 
#> [[3]]
#> [1] TRUE
#> 
#> [[4]]
#> [1] 1+4i
```

## Factors {-}

Factors are used to represent categorical data and can be unordered or ordered. One can think of a factor as an integer vector where each integer has a label. Factors are important in statistical modeling and are treated specially by modelling functions like `lm()` and `glm()`.

Using factors with labels is better than using integers because factors are self-describing. Having a variable that has values “Male” and “Female” is better than a variable that has values 1 and 2.

Factor objects can be created with the factor() function.


```r
x <- factor(c("yes", "yes", "no", "yes", "no")) 
x
#> [1] yes yes no  yes no 
#> Levels: no yes
```

Level are put in alphabetical order, but you can also define the levels. 


```r
x <- factor(c("yes", "yes", "no", "yes", "no"),levels = c("yes", "no"))
x
#> [1] yes yes no  yes no 
#> Levels: yes no
```

## Data frames: Creating and exploring data frames {-}

Data frames are used to store tabular data in R.

Data frames are represented as a special type of list where every element of the list has to have the same length. Each element of the list can be thought of as a column and the length of each element of the list is the number of rows.


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

Exercise:

Inspect a built-in data frame

```r
mtcars
#>                      mpg cyl  disp  hp drat    wt  qsec vs
#> Mazda RX4           21.0   6 160.0 110 3.90 2.620 16.46  0
#> Mazda RX4 Wag       21.0   6 160.0 110 3.90 2.875 17.02  0
#> Datsun 710          22.8   4 108.0  93 3.85 2.320 18.61  1
#> Hornet 4 Drive      21.4   6 258.0 110 3.08 3.215 19.44  1
#> Hornet Sportabout   18.7   8 360.0 175 3.15 3.440 17.02  0
#> Valiant             18.1   6 225.0 105 2.76 3.460 20.22  1
#> Duster 360          14.3   8 360.0 245 3.21 3.570 15.84  0
#> Merc 240D           24.4   4 146.7  62 3.69 3.190 20.00  1
#> Merc 230            22.8   4 140.8  95 3.92 3.150 22.90  1
#> Merc 280            19.2   6 167.6 123 3.92 3.440 18.30  1
#> Merc 280C           17.8   6 167.6 123 3.92 3.440 18.90  1
#> Merc 450SE          16.4   8 275.8 180 3.07 4.070 17.40  0
#> Merc 450SL          17.3   8 275.8 180 3.07 3.730 17.60  0
#> Merc 450SLC         15.2   8 275.8 180 3.07 3.780 18.00  0
#> Cadillac Fleetwood  10.4   8 472.0 205 2.93 5.250 17.98  0
#> Lincoln Continental 10.4   8 460.0 215 3.00 5.424 17.82  0
#> Chrysler Imperial   14.7   8 440.0 230 3.23 5.345 17.42  0
#> Fiat 128            32.4   4  78.7  66 4.08 2.200 19.47  1
#> Honda Civic         30.4   4  75.7  52 4.93 1.615 18.52  1
#> Toyota Corolla      33.9   4  71.1  65 4.22 1.835 19.90  1
#> Toyota Corona       21.5   4 120.1  97 3.70 2.465 20.01  1
#> Dodge Challenger    15.5   8 318.0 150 2.76 3.520 16.87  0
#> AMC Javelin         15.2   8 304.0 150 3.15 3.435 17.30  0
#> Camaro Z28          13.3   8 350.0 245 3.73 3.840 15.41  0
#> Pontiac Firebird    19.2   8 400.0 175 3.08 3.845 17.05  0
#> Fiat X1-9           27.3   4  79.0  66 4.08 1.935 18.90  1
#> Porsche 914-2       26.0   4 120.3  91 4.43 2.140 16.70  0
#> Lotus Europa        30.4   4  95.1 113 3.77 1.513 16.90  1
#> Ford Pantera L      15.8   8 351.0 264 4.22 3.170 14.50  0
#> Ferrari Dino        19.7   6 145.0 175 3.62 2.770 15.50  0
#> Maserati Bora       15.0   8 301.0 335 3.54 3.570 14.60  0
#> Volvo 142E          21.4   4 121.0 109 4.11 2.780 18.60  1
#>                     am gear carb
#> Mazda RX4            1    4    4
#> Mazda RX4 Wag        1    4    4
#> Datsun 710           1    4    1
#> Hornet 4 Drive       0    3    1
#> Hornet Sportabout    0    3    2
#> Valiant              0    3    1
#> Duster 360           0    3    4
#> Merc 240D            0    4    2
#> Merc 230             0    4    2
#> Merc 280             0    4    4
#> Merc 280C            0    4    4
#> Merc 450SE           0    3    3
#> Merc 450SL           0    3    3
#> Merc 450SLC          0    3    3
#> Cadillac Fleetwood   0    3    4
#> Lincoln Continental  0    3    4
#> Chrysler Imperial    0    3    4
#> Fiat 128             1    4    1
#> Honda Civic          1    4    2
#> Toyota Corolla       1    4    1
#> Toyota Corona        0    3    1
#> Dodge Challenger     0    3    2
#> AMC Javelin          0    3    2
#> Camaro Z28           0    3    4
#> Pontiac Firebird     0    3    2
#> Fiat X1-9            1    4    1
#> Porsche 914-2        1    5    2
#> Lotus Europa         1    5    2
#> Ford Pantera L       1    5    4
#> Ferrari Dino         1    5    6
#> Maserati Bora        1    5    8
#> Volvo 142E           1    4    2
str(mtcars)
#> 'data.frame':	32 obs. of  11 variables:
#>  $ mpg : num  21 21 22.8 21.4 18.7 18.1 14.3 24.4 22.8 19.2 ...
#>  $ cyl : num  6 6 4 6 8 6 8 4 4 6 ...
#>  $ disp: num  160 160 108 258 360 ...
#>  $ hp  : num  110 110 93 110 175 105 245 62 95 123 ...
#>  $ drat: num  3.9 3.9 3.85 3.08 3.15 2.76 3.21 3.69 3.92 3.92 ...
#>  $ wt  : num  2.62 2.88 2.32 3.21 3.44 ...
#>  $ qsec: num  16.5 17 18.6 19.4 17 ...
#>  $ vs  : num  0 0 1 1 0 1 0 1 1 1 ...
#>  $ am  : num  1 1 1 0 0 0 0 0 0 0 ...
#>  $ gear: num  4 4 4 3 3 3 3 4 4 4 ...
#>  $ carb: num  4 4 1 1 2 1 4 2 2 4 ...
head(mtcars)
#>                    mpg cyl disp  hp drat    wt  qsec vs am
#> Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1
#> Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1
#> Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1
#> Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0
#> Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0
#> Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0
#>                   gear carb
#> Mazda RX4            4    4
#> Mazda RX4 Wag        4    4
#> Datsun 710           4    1
#> Hornet 4 Drive       3    1
#> Hornet Sportabout    3    2
#> Valiant              3    1
```

Extract a variable from a data frame and ask a summary 

```r
summary(mtcars$cyl) # use $ to extract variable from a data frame
#>    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
#>   4.000   4.000   6.000   6.188   8.000   8.000
```

Now inspect a tibble


```r
library(ggplot2)
diamonds
#> # A tibble: 53,940 × 10
#>    carat cut     color clarity depth table price     x     y
#>    <dbl> <ord>   <ord> <ord>   <dbl> <dbl> <int> <dbl> <dbl>
#>  1  0.23 Ideal   E     SI2      61.5    55   326  3.95  3.98
#>  2  0.21 Premium E     SI1      59.8    61   326  3.89  3.84
#>  3  0.23 Good    E     VS1      56.9    65   327  4.05  4.07
#>  4  0.29 Premium I     VS2      62.4    58   334  4.2   4.23
#>  5  0.31 Good    J     SI2      63.3    58   335  4.34  4.35
#>  6  0.24 Very G… J     VVS2     62.8    57   336  3.94  3.96
#>  7  0.24 Very G… I     VVS1     62.3    57   336  3.95  3.98
#>  8  0.26 Very G… H     SI1      61.9    55   337  4.07  4.11
#>  9  0.22 Fair    E     VS2      65.1    61   337  3.87  3.78
#> 10  0.23 Very G… H     VS1      59.4    61   338  4     4.05
#> # ℹ 53,930 more rows
#> # ℹ 1 more variable: z <dbl>
str(diamonds)  # built-in in library ggplot2
#> tibble [53,940 × 10] (S3: tbl_df/tbl/data.frame)
#>  $ carat  : num [1:53940] 0.23 0.21 0.23 0.29 0.31 0.24 0.24 0.26 0.22 0.23 ...
#>  $ cut    : Ord.factor w/ 5 levels "Fair"<"Good"<..: 5 4 2 4 2 3 3 3 1 3 ...
#>  $ color  : Ord.factor w/ 7 levels "D"<"E"<"F"<"G"<..: 2 2 2 6 7 7 6 5 2 5 ...
#>  $ clarity: Ord.factor w/ 8 levels "I1"<"SI2"<"SI1"<..: 2 3 5 4 2 6 7 3 4 5 ...
#>  $ depth  : num [1:53940] 61.5 59.8 56.9 62.4 63.3 62.8 62.3 61.9 65.1 59.4 ...
#>  $ table  : num [1:53940] 55 61 65 58 58 57 57 55 61 61 ...
#>  $ price  : int [1:53940] 326 326 327 334 335 336 336 337 337 338 ...
#>  $ x      : num [1:53940] 3.95 3.89 4.05 4.2 4.34 3.94 3.95 4.07 3.87 4 ...
#>  $ y      : num [1:53940] 3.98 3.84 4.07 4.23 4.35 3.96 3.98 4.11 3.78 4.05 ...
#>  $ z      : num [1:53940] 2.43 2.31 2.31 2.63 2.75 2.48 2.47 2.53 2.49 2.39 ...
head(diamonds)
#> # A tibble: 6 × 10
#>   carat cut      color clarity depth table price     x     y
#>   <dbl> <ord>    <ord> <ord>   <dbl> <dbl> <int> <dbl> <dbl>
#> 1  0.23 Ideal    E     SI2      61.5    55   326  3.95  3.98
#> 2  0.21 Premium  E     SI1      59.8    61   326  3.89  3.84
#> 3  0.23 Good     E     VS1      56.9    65   327  4.05  4.07
#> 4  0.29 Premium  I     VS2      62.4    58   334  4.2   4.23
#> 5  0.31 Good     J     SI2      63.3    58   335  4.34  4.35
#> 6  0.24 Very Go… J     VVS2     62.8    57   336  3.94  3.96
#> # ℹ 1 more variable: z <dbl>
```


Can you list some differences?


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

