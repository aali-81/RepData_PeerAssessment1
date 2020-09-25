---
title: "Reproducible Research-Course Project 1"
author: "A.Ali"
date: "9/25/2020" 
output: 
  html_document:
    keep_md: true
---



## Loading the necessary libraries: 
# 


```r
library(datasets)
library(ggplot2)
```

## Loading and preprocessing the data
# 


```r
if(!file.exists('activity.csv')){
    unzip('activity.zip')
}
rowdata <- read.csv('activity.csv')
```

## What is mean total number of steps taken per day?


```r
StepsperDay <- aggregate(rowdata$steps, by=list(date=rowdata$date), sum)

barplot(
    StepsperDay$x,
    names.arg = StepsperDay$date,
    xlab = 'Date',
    ylab = 'Total number of steps',
    main = 'Total number of steps per day'
    )
```

![](PA1_template_files/figure-html/unnamed-chunk-3-1.png)<!-- -->

## What is the average daily activity pattern?


```r
avgStepsbyInterval <- aggregate(steps ~ interval, rowdata, mean)

plot(
    avgStepsbyInterval$interval,
    avgStepsbyInterval$steps,
    type = 'l',
    xlab = 'Intervals',
    ylab = 'Average number of steps',
    main = 'Average daily activity pattern')
```

![](PA1_template_files/figure-html/unnamed-chunk-4-1.png)<!-- -->

## Imputing missing values


```r
Missing <- sum(is.na(rowdata))

paste('Total number of missing values in this database is', Missing)
```

```
## [1] "Total number of missing values in this database is 2304"
```

## Are there differences in activity patterns between weekdays and weekends?


