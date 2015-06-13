# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data
first, we want to unzip and read the data into a data.frame

```r
unzip("activity.zip")
activity <- read.csv("activity.csv")
```
verify, that something has been loaded:

```r
names(activity)
```

```
## [1] "steps"    "date"     "interval"
```

change the `date` from a factor variable to a date variable:

```r
activity$date <- as.Date(activity$date)
```


## What is mean total number of steps taken per day?

calculate the total number of steps per day:

```r
nStepsPerDay <- aggregate(activity$steps, list(activity$date), sum)
names(nStepsPerDay) <- c("Date", "total steps")
```

here is a bar bplot for the total number of steps per day:

```r
library(ggplot2)
g <- ggplot(nStepsPerDay, aes(x=Date, y = `total steps`))
g <- g + geom_bar(stat = "identity", position = "stack")
g <- g + ggtitle("number of steps per day")
g
```

```
## Warning: Removed 8 rows containing missing values (position_stack).
```

![](PA1_template_files/figure-html/unnamed-chunk-5-1.png) 

and here is the histogram:


```r
g <- ggplot(nStepsPerDay, aes(`total steps`))
g <- g + geom_histogram()
g
```

```
## stat_bin: binwidth defaulted to range/30. Use 'binwidth = x' to adjust this.
```

![](PA1_template_files/figure-html/unnamed-chunk-6-1.png) 

the mean is:

```r
mean(nStepsPerDay$`total steps`, na.rm = T)
```

```
## [1] 10766.19
```

and the median is:

```r
median(nStepsPerDay$`total steps`, na.rm = T)
```

```
## [1] 10765
```


## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
