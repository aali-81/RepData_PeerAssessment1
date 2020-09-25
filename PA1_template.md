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
stepsByDay <- tapply(rowdata$steps, rowdata$date, sum, na.rm=TRUE)
```

## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?


