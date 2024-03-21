# Part II: Text Data Processing (30 minutes) {-}
## Manipulating and analyzing text data using regular expressions {-}


```r
# --- Part II: Text Data Processing (30 minutes) ---

# Load necessary libraries
library(stringr)

## Manipulating and analyzing text data using regular expressions

# Example: Extracting email addresses from a string
text <- "Contact us at support@example.com or feedback@example.net"
emails <- str_extract_all(text, "[[:alnum:]_.]+@[[:alnum:]]+\\.[[:alpha:]]{2,}")
print(emails)
#> [[1]]
#> [1] "support@example.com"  "feedback@example.net"
```

*Exercise*:

1. Write a regular expression to find all the words starting with 'b' in a given text.

## Text mining basics {-}


```r

# Load the 'tm' package for text mining
library(tm)
#> Loading required package: NLP

# Example: Basic text mining with a simple corpus
docs <- Corpus(VectorSource(c("Text mining is awesome", "R is a versatile tool for text analysis")))
dtm <- DocumentTermMatrix(docs)
inspect(dtm)
#> <<DocumentTermMatrix (documents: 2, terms: 7)>>
#> Non-/sparse entries: 8/6
#> Sparsity           : 43%
#> Maximal term length: 9
#> Weighting          : term frequency (tf)
#> Sample             :
#>     Terms
#> Docs analysis awesome for mining text tool versatile
#>    1        0       1   0      1    1    0         0
#>    2        1       0   1      0    1    1         1
```

*Exercise*:

2. Create a corpus from your own text data and compute its term frequency-inverse document frequency (tf-idf) matrix.


