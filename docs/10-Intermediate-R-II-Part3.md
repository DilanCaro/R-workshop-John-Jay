
# (Optional) Part V: Working with Dates and Times (20 minutes) {-}


## Handling date and time data in R {-}

R provides the Date class for dates and the POSIXct and POSIXlt classes for times.


```r
# Converting a string to a Date object
date_example <- as.Date("2021-01-01")
print(date_example)
#> [1] "2021-01-01"

# Converting a string to a POSIXct datetime object
datetime_example <- as.POSIXct("2021-01-01 10:00:00", tz = "GMT")
print(datetime_example)
#> [1] "2021-01-01 10:00:00 GMT"
```

## Common date and time functions {-}


```r

# Extracting parts of a date
year <- format(date_example, "%Y")
month <- format(date_example, "%m")
day <- format(date_example, "%d")
print(paste("Year:", year, "- Month:", month, "- Day:", day))
#> [1] "Year: 2021 - Month: 01 - Day: 01"

# Working with time intervals
start_time <- as.POSIXct("2021-01-01 08:00:00", tz = "GMT")
end_time <- as.POSIXct("2021-01-01 10:00:00", tz = "GMT")
time_diff <- difftime(end_time, start_time, units = "hours")
print(paste("Difference in hours:", time_diff))
#> [1] "Difference in hours: 2"

# Loading a dataset with date and time data for exercises
# Using the 'airquality' dataset from the 'datasets' package
data(airquality)
airquality$Date <- as.Date(with(airquality, paste(1973, Month, Day, sep = "-")))
print(head(airquality))
#>   Ozone Solar.R Wind Temp Month Day       Date
#> 1    41     190  7.4   67     5   1 1973-05-01
#> 2    36     118  8.0   72     5   2 1973-05-02
#> 3    12     149 12.6   74     5   3 1973-05-03
#> 4    18     313 11.5   62     5   4 1973-05-04
#> 5    NA      NA 14.3   56     5   5 1973-05-05
#> 6    28      NA 14.9   66     5   6 1973-05-06
```

Exercises:

```r
data(airquality)

airquality$Date <- as.Date(with(airquality, paste(1973, Month, Day, sep = "-")))
print(head(airquality))
#>   Ozone Solar.R Wind Temp Month Day       Date
#> 1    41     190  7.4   67     5   1 1973-05-01
#> 2    36     118  8.0   72     5   2 1973-05-02
#> 3    12     149 12.6   74     5   3 1973-05-03
#> 4    18     313 11.5   62     5   4 1973-05-04
#> 5    NA      NA 14.3   56     5   5 1973-05-05
#> 6    28      NA 14.9   66     5   6 1973-05-06
```

1. Convert the 'Date' column in the 'airquality' dataset to a week day and create a new column 'WeekDay'.


```r
airquality$WeekDay <- weekdays(airquality$Date)
print(head(airquality))
#>   Ozone Solar.R Wind Temp Month Day       Date   WeekDay
#> 1    41     190  7.4   67     5   1 1973-05-01   Tuesday
#> 2    36     118  8.0   72     5   2 1973-05-02 Wednesday
#> 3    12     149 12.6   74     5   3 1973-05-03  Thursday
#> 4    18     313 11.5   62     5   4 1973-05-04    Friday
#> 5    NA      NA 14.3   56     5   5 1973-05-05  Saturday
#> 6    28      NA 14.9   66     5   6 1973-05-06    Sunday
```

2. Calculate the number of days between the first and last measurements in the 'airquality' dataset.


```r
date_diff <- difftime(max(airquality$Date), min(airquality$Date), units = "days")
print(paste("Days between first and last measurement:", date_diff))
#> [1] "Days between first and last measurement: 152"
```


## Working with dates and times

## Create and format dates

To create a Date object from a simple character string in R, you can use the as.Date() function. The character string has to obey a format that can be defined using a set of symbols (the examples correspond to 13 January, 1982):

`%Y`: 4-digit year (1982)
`%y`: 2-digit year (82)
`%m`: 2-digit month (01)
`%d`: 2-digit day of the month (13)
`%A`: weekday (Wednesday)
`%a`: abbreviated weekday (Wed)
`%B`: month (January)
`%b`: abbreviated month (Jan)

For more information and a full list use `?strptime`

## as.Date()


```r
as.Date('2019-06-05',format = '%Y-%m-%d')
#> [1] "2019-06-05"
```

Dates are often stored as integers.

Convert integers to dates by speciying the origin (Day 0).

For example: SAS stores dates at the number of days elapsed since 1 Jan 1960.


```r
as.Date(21705, origin = '1960-01-01')
#> [1] "2019-06-05"
```
## Exercise 1 {-}

Work with the policy_data data set.
1. Convert the start date (debut_pol) and end date (fin_pol) into R Date objects.


```r
library(dplyr)
#> 
#> Attaching package: 'dplyr'
#> The following objects are masked from 'package:stats':
#> 
#>     filter, lag
#> The following objects are masked from 'package:base':
#> 
#>     intersect, setdiff, setequal, union
policy_data <- read.csv(file = 'John Jay Workshop Data/PolicyData.csv', sep = ';')
policy_data$start <- as.Date(policy_data$debut_pol, '%d/%m/%Y')
policy_data$end <- as.Date(policy_data$fin_pol, '%d/%m/%Y')
head(policy_data %>% select(c('debut_pol', 'start')))
#>    debut_pol      start
#> 1 14/09/1995 1995-09-14
#> 2 25/04/1996 1996-04-25
#> 3  1/03/1995 1995-03-01
#> 4  1/03/1996 1996-03-01
#> 5 15/01/1997 1997-01-15
#> 6  1/02/1997 1997-02-01
```

## format() {-}


```r
today <- as.Date('2019-06-05',
                format = '%Y-%m-%d')
format(today, '%A %d %B %Y')
#> [1] "Wednesday 05 June 2019"
```

Calculate the duration of a contract.


```r
policy_duration =
  policy_data$end - policy_data$start
```

You can add and subtract integers from dates.

```r
tomorrow = today + 1
print(tomorrow)
#> [1] "2019-06-06"
```

## Lubridate {-}

## Access date components

```r
# install.packages("lubridate")
library(lubridate)
#> 
#> Attaching package: 'lubridate'
#> The following objects are masked from 'package:base':
#> 
#>     date, intersect, setdiff, union
```


```r
year(today)
#> [1] 2019
```
Other components are: month(), day(), quarter(), ...

## Advanced math

```r
today + months(3)
#> [1] "2019-09-05"
```
Other periods are: years() and days().



```r
floor_date(today, unit = "month")
#> [1] "2019-06-01"
```
floor_date rounds down to the nearest unit. 

In the example convert daily into monthly data.

## seq() {-}


```r
seq(from = as.Date('2019-01-01'),
    to = as.Date('2019-12-31'),
    by = '1 month')
#>  [1] "2019-01-01" "2019-02-01" "2019-03-01" "2019-04-01"
#>  [5] "2019-05-01" "2019-06-01" "2019-07-01" "2019-08-01"
#>  [9] "2019-09-01" "2019-10-01" "2019-11-01" "2019-12-01"
```

## Exercise 2 {-}

Visualize the exposure contribution by start month of the contract in the policy_data data set.
1. Add a covariate start_month to the data set. 2. Group the data by start_month.
3. Calculate the exposure within each group.
4. Plot the data.

