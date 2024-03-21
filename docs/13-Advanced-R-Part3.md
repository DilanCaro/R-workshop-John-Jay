# Part III: Building Predictive Models (30 minutes){-}
## Introduction to machine learning in R {-}

*Brief overview of machine learning:* Machine learning in R involves using statistical techniques to enable computers to improve at tasks with experience. It encompasses a variety of techniques for classification, regression, clustering, and more.


```r
# Load necessary libraries
#install.packages("caret")
library(caret)
#> Loading required package: ggplot2
#> Loading required package: lattice


# Example: Splitting a dataset into training and testing sets
data(iris)
set.seed(123) # Setting seed for reproducibility
trainingIndex <- createDataPartition(iris$Species, p = 0.8, list = FALSE)
trainingData <- iris[trainingIndex, ]
testingData <- iris[-trainingIndex, ]

```

*Exercise*:

1. Load a different dataset and partition it into training and testing sets.

## Creating predictive models with caret {-}


```r

# Example: Building a predictive model for the iris dataset
model <- train(Species ~ ., data = trainingData, method = "rpart")
print(model)
#> CART 
#> 
#> 120 samples
#>   4 predictor
#>   3 classes: 'setosa', 'versicolor', 'virginica' 
#> 
#> No pre-processing
#> Resampling: Bootstrapped (25 reps) 
#> Summary of sample sizes: 120, 120, 120, 120, 120, 120, ... 
#> Resampling results across tuning parameters:
#> 
#>   cp    Accuracy   Kappa    
#>   0.00  0.9398492  0.9086993
#>   0.45  0.7426390  0.6253355
#>   0.50  0.5557896  0.3665192
#> 
#> Accuracy was used to select the optimal model using
#>  the largest value.
#> The final value used for the model was cp = 0.

# Predicting using the model
predictions <- predict(model, testingData)
confusionMatrix(predictions, testingData$Species)
#> Confusion Matrix and Statistics
#> 
#>             Reference
#> Prediction   setosa versicolor virginica
#>   setosa         10          0         0
#>   versicolor      0         10         2
#>   virginica       0          0         8
#> 
#> Overall Statistics
#>                                           
#>                Accuracy : 0.9333          
#>                  95% CI : (0.7793, 0.9918)
#>     No Information Rate : 0.3333          
#>     P-Value [Acc > NIR] : 8.747e-12       
#>                                           
#>                   Kappa : 0.9             
#>                                           
#>  Mcnemar's Test P-Value : NA              
#> 
#> Statistics by Class:
#> 
#>                      Class: setosa Class: versicolor
#> Sensitivity                 1.0000            1.0000
#> Specificity                 1.0000            0.9000
#> Pos Pred Value              1.0000            0.8333
#> Neg Pred Value              1.0000            1.0000
#> Prevalence                  0.3333            0.3333
#> Detection Rate              0.3333            0.3333
#> Detection Prevalence        0.3333            0.4000
#> Balanced Accuracy           1.0000            0.9500
#>                      Class: virginica
#> Sensitivity                    0.8000
#> Specificity                    1.0000
#> Pos Pred Value                 1.0000
#> Neg Pred Value                 0.9091
#> Prevalence                     0.3333
#> Detection Rate                 0.2667
#> Detection Prevalence           0.2667
#> Balanced Accuracy              0.9000
```

*Exercise*:
2. Build a predictive model for another dataset and evaluate its performance.


```

