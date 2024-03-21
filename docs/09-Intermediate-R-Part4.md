
# Part IV: Statistical Analysis (30 minutes) {-}


## Introduction to hypothesis testing and statistical tests {-}


Hypothesis testing is a statistical method used to make inferences or draw conclusions about a population based on sample data. It starts with a null hypothesis (H0) that assumes no effect or no difference, and an alternative hypothesis (H1) that contradicts the null hypothesis.

The process involves:
1. Defining the null and alternative hypotheses.
2. Selecting a significance level (alpha, typically 0.05).
3. Calculating a test statistic based on the sample data.
4. Determining the p-value, which is the probability of observing the test statistic or something more extreme under the null hypothesis.
5. Comparing the p-value with the significance level to decide whether to reject the null hypothesis.

Statistical tests vary based on the type of data and the research question. Common tests include t-tests (for means), chi-squared tests (for categorical data), ANOVA (for comparing means across multiple groups), and regression analysis (for relationships between variables).




## Performing t-tests and chi-squared tests {-}

```r
# Load necessary libraries
library(stats)

# Example: Performing a t-test
# Hypothesis: The mean of a sample is different from the population mean (which we assume to be 0 for this example).

sample_data <- rnorm(30)  # Generating a sample of 30 random normal numbers
t_test_result <- t.test(sample_data, mu = 0)  # Performing a one-sample t-test
print(t_test_result)
#> 
#> 	One Sample t-test
#> 
#> data:  sample_data
#> t = -0.66944, df = 29, p-value = 0.5085
#> alternative hypothesis: true mean is not equal to 0
#> 95 percent confidence interval:
#>  -0.4735027  0.2399700
#> sample estimates:
#>  mean of x 
#> -0.1167663

# Example: Performing a chi-squared test
# Hypothesis: Two categorical variables are independent.

# Creating a sample contingency table
observed <- matrix(c(10, 10, 20, 20), nrow = 2, byrow = TRUE)
dimnames(observed) <- list(gender = c("Male", "Female"), preference = c("Option A", "Option B"))

chi_squared_test_result <- chisq.test(observed)  # Performing the chi-squared test
print(chi_squared_test_result)
#> 
#> 	Pearson's Chi-squared test
#> 
#> data:  observed
#> X-squared = 0, df = 1, p-value = 1
```
