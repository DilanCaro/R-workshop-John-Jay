# Part II: R Fundamentals {-}

Before starting, here are some Official manuals and books we will be learning from :

1. https://cran.r-project.org/doc/manuals/r-release/R-intro.html
1. https://cran.r-project.org/doc/manuals/r-release/R-data.html
1. https://cran.r-project.org/doc/manuals/r-release/R-exts.html
1. https://cran.r-project.org/doc/manuals/r-release/R-lang.html
1. [R programming for Data Science by Roger D. Peng.](https://bookdown.org/rdpeng/rprogdatascience/)
1. [R for Data Science](https://r4ds.had.co.nz/)

### R as a calculator {-}

The best way to get used to R is to use it as a calculator.

You can start by using the R console and doing simple operations. 

### Basic arithmetic operations {-}

- Addition

```r
3+5
#> [1] 8
```
- Subtraction

```r
143-12
#> [1] 131
```
- Multiplication

```r
4*5
#> [1] 20
```
- Division

```r
180/23
#> [1] 7.826087
```
- Exponientiation

```r
4^2
#> [1] 16
```

#### Arithmetic Functions {-}

this functions may be useful to replace your calculator

- Absolute value 

```r
abs(-23)
#> [1] 23
```
- Square root

```r
sqrt(16)
#> [1] 4
```
- Remainder/modulo 

```r
7 %% 3
#> [1] 1
```

- Logarithms and exponentials 
i.e, 

$$\log_a b = c,\quad ln_e b=a , \quad  e^{a}=b$$

```r
log2(4)
#> [1] 2
log10(1000)
#> [1] 3
log(4)
#> [1] 1.386294
exp(8)
#> [1] 2980.958
2.71828^8
#> [1] 2980.942
```


### Variables and data types (numeric,character) {-}

#### Assigment Operators {-}
 in `R`, to create a variable , you can use the assigment symbol `<-`, or `=` however, the later is not commonly used in `R`. 
 
 To assign the value of 7 to x , we will do 
 

```r
x <- 7
print(x)
#> [1] 7
```
 
We can now perform operations on these variables

```r
3*x+3 # 3*7+3 = 21+3 =24
#> [1] 24
```

**Remark:** R is case sensitive so, `x` is different from `X`

calling `print(X)` will output error

```r
print(X)
#> Error in eval(expr, envir, enclos): object 'X' not found
```

#### Data types {-}

R has five basic or "atomic" classes of objects:

- character
- numeric (real numbers) 
- integer
- complex
- logical (True/False)

#### Exercise {-}


```r
my_numeric <- 42.5
John_jay <- "university"
my_logical <- TRUE
my_date <- as.Date("05/29/2018", "%m/%d/%Y")
typeof(my_date)
#> [1] "double"
class(my_date)
#> [1] "Date"
```

Use `typeof()` function to find out what the data type of a variable is .
**Character Data type ** 
A character stores character values or strings 

```r
char <- "This is a character data type"
char
#> [1] "This is a character data type"
typeof(char)
#> [1] "character"
```

**Numeric Data type ** 
This is for numerical values .


```r
num <- 3
print(num)
#> [1] 3
num_2 <- -2.35
num_2
#> [1] -2.35
typeof(num_2)
#> [1] "double"
class(num_2)
#> [1] "numeric"
```

**Integer Data type** 
For integers, we must specify it as so, and to do it , we must convert the data type. Remark: if it is a decimal, it will remove all decimal, acting as a floor function . 


```r
int <- as.integer(3.6332)
int
#> [1] 3
typeof(int)
#> [1] "integer"
int2 <- as.integer(7)
int2
#> [1] 7
typeof(int2)
#> [1] "integer"
class(int2)
#> [1] "integer"
```

We can also create a integer by adding an L after it 


```r
int3 <- 8L
int3
#> [1] 8
```
Remark: It does not work with decimals 

```r
int4 <- 3.4546L
int4
#> [1] 3.4546
```

**Complex Data type** 
Complex data types are stored as `x+yi` , i.e, with the imaginary component

```r
compl <- 13+7i
compl
#> [1] 13+7i
typeof(compl)
#> [1] "complex"
complex(real = 23, imaginary = 7)
#> [1] 23+7i
```


**Boolean Data type ** 
This stores boolean values of `TRUE` and `FALSE`


```r
my_bool <- TRUE
my_bool
#> [1] TRUE

typeof(my_bool)
#> [1] "logical"

my_boolean <- F
my_boolean
#> [1] FALSE
typeof(my_boolean)
#> [1] "logical"
```

#### Converting Data types {-}

**Convert into Numeric**

We can convert values as numeric. Using `as.numeric()` to change the type but keeping the values as they are. 
When converting 

- complex: removes the `imaginary` part
- logical: `TRUE` becomes `1` , `FALSE` becomes `0`
- character: to its numerical values, but if it has letters then to `NA`

We can use `is.numeric()` to check if a variable is numeric 


```r
# Complex
is.numeric(compl)
#> [1] FALSE
number <- as.numeric(compl)
#> Warning: imaginary parts discarded in coercion
number
#> [1] 13
is.numeric(number)
#> [1] TRUE

#Logical 
is.numeric(my_bool)
#> [1] FALSE
number2 <- as.numeric(my_bool)
number2
#> [1] 1
is.numeric(number2)
#> [1] TRUE

# Character
char
#> [1] "This is a character data type"
is.numeric(char)
#> [1] FALSE
number3 <- as.numeric(char)
#> Warning: NAs introduced by coercion
number3
#> [1] NA
is.numeric(number3)
#> [1] TRUE

my_char <- "2023"
is.numeric(my_char)
#> [1] FALSE
number4 <- as.numeric(my_char)
number4
#> [1] 2023
is.numeric(number4)
#> [1] TRUE
```

**Convert into integer**


```r
inte1<-as.integer("234")
inte1
#> [1] 234
typeof(inte1)
#> [1] "integer"

inte2<-as.integer(23+6i)
#> Warning: imaginary parts discarded in coercion
inte2
#> [1] 23
typeof(inte2)
#> [1] "integer"

inte3<-as.integer(F)
inte3
#> [1] 0
typeof(inte3)
#> [1] "integer"
```

**Converting into Logical**

Return `FALSE` for `0` , `TRUE` otherwise

```r
print(as.logical(0))
#> [1] FALSE
typeof(as.logical(0))
#> [1] "logical"

print(as.logical(-324))
#> [1] TRUE
typeof(as.logical(-324))
#> [1] "logical"
```



### Getting help {-}

You can use the Plots and files pane (bottom left pane) to click on Help and then search for whichever function you need help with. 

You can also use the `?` before each function. 


```r
?mean
```
This will open the information about the function on the plots and files pane.



