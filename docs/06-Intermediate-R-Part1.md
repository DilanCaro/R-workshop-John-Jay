# Intermediate R {-}

# Part I: Functions and Control Structures (30 minutes) {-}

## Writing and using functions {-}


```r
# Example: A simple function to calculate the square of a number
square_function <- function(x) {
  return(x^2)
}

# Using the function
result <- square_function(4)
print(result)
#> [1] 16
```

## If statements and loops (for and while) {-}


```r
# Example: Using if statement
number <- 5
if (number > 0) {
  print("Positive number")
} else {
  print("Non-positive number")
}
#> [1] "Positive number"

# Example: For loop to calculate the factorial of a number
factorial_function <- function(n) {
  result <- 1
  for (i in 1:n) {
    result <- result * i
  }
  return(result)
}

factorial_of_5 <- factorial_function(5)
print(factorial_of_5)
#> [1] 120

# Example: While loop to find the first square number greater than 100
number <- 1
while (number^2 <= 100) {
  number <- number + 1
}
print(paste("First square number greater than 100 is:", number^2))
#> [1] "First square number greater than 100 is: 121"
```

