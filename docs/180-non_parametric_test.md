




```{=tex}

\section*{Testing the Mean Length of Bolts}

To conduct a distribution-free test to determine if the mean length of manufactured bolts differs from 5 cm, we utilize a non-parametric test such as the \textbf{Wilcoxon Signed-Rank Test}. This test does not assume a normal distribution of the bolt lengths.

\subsection*{Steps to Conduct the Test}

\textbf{Formulate Hypotheses}:
\begin{itemize}
  \item Null Hypothesis ($H_0$): The median length of the bolts is 5 cm.
  \item Alternative Hypothesis ($H_a$): The median length of the bolts is not 5 cm.
\end{itemize}

\textbf{Collect Sample Data}:
Assume we collect a sample of bolt lengths: [6, 7, 7.5, 5.1, 4.9, 5.2, 6.1, 6.5, 6.8, 7].

\textbf{Calculate Test Statistic}:
\begin{enumerate}
  \item Calculate the difference from 5 cm for each bolt length.
  \item Rank the absolute differences, ignoring zeros (exact matches with 5 cm).
  \item Assign signs to the ranks based on whether the sample value is greater or less than 5 cm.
  \item Sum the ranks for positive and negative differences.
\end{enumerate}

\textbf{Determine the Critical Region and p-value}:
\begin{itemize}
  \item Use tables for the Wilcoxon Signed-Rank Test to find the critical values for the sum of ranks, based on the chosen significance level ($\alpha$), typically 0.05 for a two-tailed test.
  \item Alternatively, use software or statistical packages to compute the exact p-value.
\end{itemize}

\subsection*{Example Calculation}

Using the sample data [6, 7, 7.5, 5.1, 4.9, 5.2, 6.1, 6.5, 6.8, 7], and $H_0$ states that the median length is 5 cm.

\textbf{Data Processing}:
\begin{itemize}
  \item Differences from 5 cm: [1, 2, 2.5, 0.1, -0.1, 0.2, 1.1, 1.5, 1.8, 2]
  \item Absolute Differences: [1, 2, 2.5, 0.1, 0.1, 0.2, 1.1, 1.5, 1.8, 2]
  \item Ranks: [2, 4.5, 8, 1, 1, 1.5, 3, 5, 7, 4.5] (ties broken by averaging ranks)
  \item Signs: [+1, +1, +1, +1, -1, +1, +1, +1, +1, +1]
  \item Sum of positive ranks: 2+4.5+8+1+1.5+3+5+7+4.5 = 36.5
  \item Sum of negative ranks: 1
\end{itemize}

\textbf{Critical Values and p-value}:
Using a Wilcoxon Signed-Rank Table, with $n = 10$, the critical value for a two-tailed test at $\alpha = 0.05$ is usually around 8 (exact values depend on tables or software used). Since the sum of positive ranks (36.5) is much higher than the critical value and dominates the negative rank sum (1), the test statistic will lead to rejecting $H_0$ if we use typical critical values.


```

```{=tex}
\textbf{P-value Calculation}:
Using statistical software, we find that the p-value for a sum of ranks is very low (0.009252) , confirming the decision to reject $H_0$.

```


```r
# Sample data for the lengths of bolts
bolt_lengths <- c(6, 7, 7.5, 5.1, 4.9, 5.2, 6.1, 6.5, 6.8, 7)

# Perform the Wilcoxon Signed-Rank Test
# H0: median bolt length = 5 cm
# Ha: median bolt length != 5 cm
test_result <- wilcox.test(bolt_lengths, mu = 5, alternative = "two.sided", conf.int = TRUE)
#> Warning in wilcox.test.default(bolt_lengths, mu = 5,
#> alternative = "two.sided", : cannot compute exact p-value
#> with ties
#> Warning in wilcox.test.default(bolt_lengths, mu = 5,
#> alternative = "two.sided", : cannot compute exact
#> confidence interval with ties

# Output the results
print(test_result)
#> 
#> 	Wilcoxon signed rank test with continuity correction
#> 
#> data:  bolt_lengths
#> V = 53.5, p-value = 0.009252
#> alternative hypothesis: true location is not equal to 5
#> 95 percent confidence interval:
#>  5.500024 6.999965
#> sample estimates:
#> (pseudo)median 
#>            6.2

# Extract and print the p-value explicitly
cat("P-value:", test_result$p.value, "\n")
#> P-value: 0.009252446
```

```{=tex}
\subsection*{Conclusion}
Based on the test, we reject the null hypothesis that the median length of the bolts is 5 cm, suggesting the alternative that the median is different from 5 cm is more likely. In reality, since the mean of the provided sample would calculate to something considerably higher than 5 cm (e.g., 6.21 cm), our test aligns with the practical observation that the bolts are longer on average, demonstrating the power of non-parametric tests in practical engineering applications.


```





