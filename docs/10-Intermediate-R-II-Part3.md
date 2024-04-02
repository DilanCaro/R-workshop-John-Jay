
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

