# Workshop 1: Suplementary Exercises Solved{-}

These exercises are from https://intro2r.com/

There are links in which more explanation is found , additionally, you can read the book and chapters you are interested in for a more detailed explanation that relates more closely to these exercises. 



\  

1. Now to practice writing code in the script editor and sourcing this code into the R console. Let's display the help file for the function `mean`. In your script type `help('mean')` and source this code into the console. Notice that the help file is displayed in the bottom right window (if not then click on the 'Help' tab). Examine the different components of the help file (especially the examples section at the end of the help file). See [Section 2.5](https://intro2r.com/help.html) of the Introduction to R book for more details on using the help functions.


```r
    help(mean)          # different methods of using help
    ?mean
    help("mean")
```


\  

2. The content displayed in the bottom right window is context dependent. For example if we write the code `plot(1:10)` in our script and then source it into the R console the bottom right window will display this plot (don't worry about understanding the R code right now, hopefully this will become clear later on in the course!). 


```r
    plot(1:10)    #dont worry about what 1:10 does just yet
```

<img src="150-SOLVED-Opt-Workshop-1-Exercises_files/figure-html/unnamed-chunk-3-1.png" width="672" />

\  

3. Next, let's practice creating a variable and assigning a value to this variable. Take a look at [Section 2.2](https://intro2r.com/objects-in-r.html) of the Introduction to R book for further information on how to do this or if you prefer watch the [Objects in R video](https://alexd106.github.io/BI5009/howto.html#objs-vid). Create a variable called `first_num` and assign it the value `42`. Click on the 'Environment' tab in the top right window to display the variable and value. Now create another variable called `first_char` and assign it a value `"my first character"`. Notice this variable is now also displayed in the 'Environment' along with it's value and class (`chr` - short for character class). 


```r
    first_num <- 42    # create variable first_num and assign the value 42
    first_char <- "my first character"
```
    
\  

4. Remove the variable `first_num` from your environment using the `rm()` function. Use the code `rm(first_num)` to do this. Check out the 'Environment' tab to ensure the variable has been removed. Alternatively, use the `ls()` function to list all objects in your environment. 

```r
    rm(first_num)
    ls()          # list all variables in the workspace 
#> [1] "first_char"
```

\  

5. Let's see what happens if we assign another value to an existing variable. Assign the value `"my second character"` to the variable `first_char` you created in Q6. Notice the value has changed in the 'Environment'. To display the value of `first.char` enter the name of the variable in the console. Don't to forget to save your R script periodically!


```r
    first_char <- "my second variable"
    first_char    # display the value 
#> [1] "my second variable"
```


\  

6. OK, let's leave RStudio for a minute. Using your favourite web browser, navigate to the [R-project website](http://www.r-project.org) and explore links that catch your eye. Make sure you find the R manuals page and the user contributed documents section. Download any manuals that you think you might find useful (some are listed in the course manual) and save them on your computer (or USB drive).

\  

7. Click on the 'Search' link on the R-Project website. Use 'Rseek' to search for the term 'mixed model p values' (this is a controversial subject!) and explore anything that looks interesting. Also experiment with the 'R site search' and 'Nabble R Forum' links. Learning how to search for help when you run into a problem when using R is an acquired skill and something you get better at over time. One note of caution, often you will find many different solutions to solving a problem in R, some written by experienced R users and others by people with less experience. Whichever solution you choose make sure you understand what the code is doing and thoroughly test it to make sure it's doing what you want.

\  

8.	OK, back to RStudio. Sometimes you may forget the exact name of a function you want to use so it would be useful to be able to search through all the function names. For example, you want to create a design plot but can only remember that the name of the function has the word 'plot' in it. Use the `apropos()` function to list all the functions with the word plot in their name (see [Section 2.5.1](https://intro2r.com/help.html#help) of the Introduction to R book). Look through the list and once you have figured what the correct function is then bring up the help file for this function (Hint: the function name probably has the words 'plot' and 'design' in it!). 

    
    ```r
    apropos("plot")
    #>  [1] "assocplot"           "barplot"            
    #>  [3] "barplot.default"     "biplot"             
    #>  [5] "boxplot"             "boxplot.default"    
    #>  [7] "boxplot.matrix"      "boxplot.stats"      
    #>  [9] "cdplot"              "coplot"             
    #> [11] "fourfoldplot"        "interaction.plot"   
    #> [13] "lag.plot"            "matplot"            
    #> [15] "monthplot"           "mosaicplot"         
    #> [17] "plot"                "plot"               
    #> [19] "plot.default"        "plot.design"        
    #> [21] "plot.ecdf"           "plot.function"      
    #> [23] "plot.new"            "plot.spec.coherency"
    #> [25] "plot.spec.phase"     "plot.stepfun"       
    #> [27] "plot.ts"             "plot.window"        
    #> [29] "plot.xy"             "preplot"            
    #> [31] "qqplot"              "recordPlot"         
    #> [33] "replayPlot"          "savePlot"           
    #> [35] "screeplot"           "spineplot"          
    #> [37] "sunflowerplot"       "termplot"           
    #> [39] "ts.plot"
    help('plot.design')
    ```
\  

9. Another strategy would be to use the `help.search()` function to search through R's help files. Search the R help system for instances of the character string ‘plot’. Take a look at [Section 2.5.1](https://intro2r.com/help.html#r-help) for more information. Also, see if you can figure out how to narrow your search by only searching for ‘plot’ in the `nlme` package (hint: see the help page for `help.search()`).

    
    ```r
    help.search("plot")
    ??plot     # shortcut for help.search function
    
    help.search("plot", package = "nlme")
    ```
\  

10.	R's working directory is the default location of any files you read into R, or export from R. Although you won't be importing or exporting files just yet (that's tomorrows job) it's useful to be able to determine what your current working directory is. So, read [Section 1.7](https://intro2r.com/work-d.html) of the Introduction to R book to introduce yourself to working directories and figure out how to display your current working directory.

    
    ```r
    getwd()    # displays the current working directory 
    #> [1] "/Users/dilancaro/Library/Mobile Documents/com~apple~CloudDocs/Workshops/John Jay/R Workshop/R-workshop-John-Jay"
    ```
\  



##Basic R operations {-}


\
Read [Chapter 2](https://intro2r.com/basics-r.html) to help you complete the questions in this exercise.

\  
11. Let's use R as a fancy calculator. Find the natural log, log to the base 10, log to the base 2, square root and the natural antilog of 12.43. See [Section 2.1](https://intro2r.com/getting-started.html#getting-started) of the Introduction to R book for more information on mathematical functions in R. Don't forget to write your code in RStudio's script editor and source the code into the console.


```r
    log(12.43)              # natural log
#> [1] 2.520113
    log10(12.43)            # log to base 10
#> [1] 1.094471
    log2(12.43)             # log to base 2
#> [1] 3.635754
    log(12.43, base = 2)    # alternative log to base 2
#> [1] 3.635754
    sqrt(12.43)             # square root
#> [1] 3.525621
    exp(12.43)              # exponent
#> [1] 250196
```
    
\  

12. Next, use R to determine the area of a circle with a diameter of 20 cm and assign the result to an object called `area_circle`. If you can't remember how to create and assign objects see [Section 2.2](https://intro2r.com/objects-in-r.html#objects-in-r) or watch this [video](https://alexd106.github.io/BI5009/howto.html#objs-vid). Google is your friend if you can't remember the formula to calculate the area of a circle! Also, remember that R already knows about `pi`. Don’t worry if you’re stumped and feel free to ask one of the instructors for guidance.


```r
    area_circle <- pi * (20/2)^2
```

\  

13. Now for something a little more tricky. Calculate the cube root of 14 x 0.51. You might need to think creatively for a solution (hint: think exponents), and remember that R follows the usual order of mathematical operators so you might need to use brackets in your code (see [this page ](https://en.wikipedia.org/wiki/Order_of_operations) if you've never heard of this). The point of this question is not to torture you with maths (so please don't stress!), its to get you used to writing mathematical equations in R and highlight the order of operations.


```r
    (14 * 0.51)^(1/3)
#> [1] 1.9256
```
    
\  

14. Ok, you're now ready to explore one of R's basic (but very useful) data structures - vectors. A vector is a sequence of elements (or components) that are all of the same data type (see [Section 3.2.1](https://intro2r.com/data-structures.html#scal_vecs) for an introduction to vectors). Although technically not correct it might be useful to think of a vector as something like a single column in a spreadsheet. There are a multitude of ways to create vectors in R but you will use the concatenate function `c()` to create a vector called `weight` containing the weight (in kg) of 10 children: `69, 62, 57, 59, 59, 64, 56, 66, 67, 66` ([Section 2.3](https://intro2r.com/using-functions-in-r.html#using-functions-in-r) or watch this [video](https://alexd106.github.io/BI5009/howto.html#vec-vid) for more information). 


```r
    weight <- c(69, 62, 57, 59, 59, 64, 56, 66, 67, 66)
```

\  

15. Now you can do some useful stuff to your `weight` vector. Get R to calculate the mean, variance, standard deviation, range of weights and the number of children of your `weight` vector (see [Section 2.3](https://intro2r.com/using-functions-in-r.html) for more details). Now read [Section 2.4](https://intro2r.com/vectors.html) of the R book to learn how to work with vectors. After reading this section you should be able to extract the weights for the first five children using [Positional indexes](https://intro2r.com/vectors.html#positional-index) and store these weights in a new variable called `first_five`. Remember, you will need to use the square brackets `[ ]` to extract (aka index, subset) elements from a variable.


```r
    mean(weight)                                # calculate mean 
#> [1] 62.5
    var(weight)                                 # calculate variance
#> [1] 20.72222
    sd(weight)                                  # calculate standard deviation
#> [1] 4.552167
    range(weight)                               # range of weight values
#> [1] 56 69
    length(weight)                              # number of observations
#> [1] 10
    
    first_five <- weight[1:5]                  # extract first 5 weight values
    first_five <- weight[c(1, 2, 3, 4, 5)]     # alternative method
```
    
\  

16. We're now going to use the the `c()` function again to create another vector called `height` containing the height (in cm) of the same 10 children: `112, 102, 83, 84, 99, 90, 77, 112, 133, 112`. Use the `summary()` function to summarise these data in the `height` object. Extract the height of the 2nd, 3rd, 9th and 10th child and assign these heights to a variable called `some_child` (take a look at the section [Positional indexes](https://intro2r.com/vectors.html#positional-index) in the R book if you're stuck). We can also extract elements using [Logical indexes](https://intro2r.com/vectors.html#logical-index). Let's extract all the heights of children less than or equal to 99 cm and assign to a variable called `shorter_child`.


```r
    height <- c(112, 102, 83, 84, 99, 90, 77, 112, 133, 112)
    
    summary(height)   # summary statistics of height variable
#>    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
#>    77.0    85.5   100.5   100.4   112.0   133.0
    
    some_child <- height[c(2, 3, 9, 10)]      # extract the 2nd, 3rd, 9th, 10th height
    
    shorter_child <- height[height <= 99]     # extract all heights less than or equal to 99
```
    
\  

17. Now you can use the information in your `weight` and `height` variables to calculate the body mass index (BMI) for each child. The BMI is calculated as weight (in kg) divided by the square of the height (in meters). Store the results of this calculation in a variable called `bmi`. Note: you don’t need to do this calculation for each child individually, you can use both vectors in the BMI equation  – this is called vectorisation (see [Section 2.4.4](https://intro2r.com/vectors.html#vectorisation) of the Introduction to R book).


```r
    bmi <- weight/(height/100)^2    # don't forget to convert height to meters
```
\  

18. Now let's practice a very useful skill - creating sequences (honestly it is...). Take a look at [Section 2.3](https://intro2r.com/using-functions-in-r.html#using-functions-in-r) in the R book (the bit on creating sequences) to see the myriad ways you can create sequences in R. Let's use the `seq()` function to create a sequence of numbers ranging from 0 to 1 in steps of 0.1 (this is also a vector by the way) and assign this sequence to a variable called `seq1`.


```r
    seq1 <- seq(from = 0, to = 1, by = 0.1)
```
\  

19.	Next, see if you can figure out how to create a sequence from 10 to 1 in steps of 0.5. Assign this sequence to a variable called `seq2` (Hint: you may find it useful to include the `rev()` function in your code).


```r
    seq2 <- rev(seq(from = 1, to = 10, by = 0.5))
```

\  

20.	Let's go sequence crazy! Generate the following sequences. You will need to experiment with the arguments to the `rep()` function to generate these sequences (see [Section 2.3](https://intro2r.com/using-functions-in-r.html#using-functions-in-r) for some clues):

- 1 2 3 1 2 3 1 2 3
- "a" "a" "a" "c" "c" "c" "e" "e" "e" "g" "g" "g"
- "a" "c" "e" "g" "a" "c" "e" "g" "a" "c" "e" "g"
- 1 1 1 2 2 2 3 3 3 1 1 1 2 2 2 3 3 3
- 1 1 1 1 1 2 2 2 2 3 3 3 4 4 5
- 7 7 7 7 2 2 2 8 1 1 1 1 1


```r
    rep(1:3, times = 3)
#> [1] 1 2 3 1 2 3 1 2 3
    rep(c("a", "c", "e", "g"), each = 3)
#>  [1] "a" "a" "a" "c" "c" "c" "e" "e" "e" "g" "g" "g"
    rep(c("a", "c", "e", "g"), times = 3)
#>  [1] "a" "c" "e" "g" "a" "c" "e" "g" "a" "c" "e" "g"
    rep(1:3, each = 3, times = 2)
#>  [1] 1 1 1 2 2 2 3 3 3 1 1 1 2 2 2 3 3 3
    rep(1:5, times = 5:1)
#>  [1] 1 1 1 1 1 2 2 2 2 3 3 3 4 4 5
    rep(c(7, 2, 8, 1), times = c(4, 3, 1, 5))
#>  [1] 7 7 7 7 2 2 2 8 1 1 1 1 1
```
    
\  

21.	Ok, back to the variable `height` you created in Q7. Let's sort the values of `height` into ascending order (shortest to tallest) and assign the sorted vector to a new variable called `height_sorted`. Take a look at [Section 2.4.3](https://intro2r.com/vectors.html#vec_ord) in the R book to see how to do this. Now sort all heights into descending order and assign the new vector a name of your choice.


```r
    height_sorted <- sort(height)
    
    height_rev <- rev(sort(height))
```

\  

22. Let's give the children some names. Create a new vector called `child_name` with the following names of the 10 children: `"Alfred", "Barbara", "James", "Jane", "John", "Judy", "Louise", "Mary", "Ronald", "William"`.


```r
    child_name <- c("Alfred", "Barbara", "James", "Jane", "John", "Judy", "Louise", "Mary", "Ronald", "William")
```
    
\  

23. A really useful (and common) task is to order the values of one variable by the order of another variable. To do this you will need to use the `order()` function in combination with the square bracket notation `[ ]`. Have a peep at [Section 2.4.3](https://intro2r.com/vectors.html#vec_ord) for some details. Create a new variable called `names_sort` to store the names of the children ordered by child height (from shortest to tallest). Who is the shortest? who is the tallest child? If you're not sure how to do this, please ask one of the instructors.



```r
    height_ord <- order(height)   # get the indexes of the heights, smallest to tallest
    names_sort <- child_name[height_ord]     # Louise is shortest, Ronald is tallest
```

\  

24. Now order the names of the children by **descending** values of weight and assign the result to a variable called `weight_rev` (Hint: perhaps include the `rev()` function?). Who is the heaviest? Who is the lightest?


```r
    weight_ord <- rev(order(weight))
    weight_rev <- child_name[weight_ord]     # Alfred is heaviest, Louise is lightest
```
\  


25. Finally, list all variables in your workspace that you have created in this exercise. Remove the variable `seq1` from the workspace using the `rm()` function. 


```r
    ls()          # list all variables in workspace
#>  [1] "area_circle"   "bmi"           "child_name"   
#>  [4] "first_char"    "first_five"    "height"       
#>  [7] "height_ord"    "height_rev"    "height_sorted"
#> [10] "names_sort"    "seq1"          "seq2"         
#> [13] "shorter_child" "some_child"    "weight"       
#> [16] "weight_ord"    "weight_rev"
    rm(seq1)      # remove variable seq1 from the workspace
    ls()          # check seq1 has been removed
#>  [1] "area_circle"   "bmi"           "child_name"   
#>  [4] "first_char"    "first_five"    "height"       
#>  [7] "height_ord"    "height_rev"    "height_sorted"
#> [10] "names_sort"    "seq2"          "shorter_child"
#> [13] "some_child"    "weight"        "weight_ord"   
#> [16] "weight_rev"
```
    
\  




