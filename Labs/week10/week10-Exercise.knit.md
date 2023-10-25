---
title: "Laboratory Exercise Week 10"
author: "Brian Tipton - STAT380-001"
date: "10/25/23"
output:
  pdf_document: default
---



*Directions*: 

* Write your R code inside the code chunks after each question.
* Write your answer comments after the `#` sign.
* To generate the word document output, click the button `Knit` and wait for the word document to appear.
* RStudio will prompt you (only once) to install the `knitr` package.
* Submit your completed laboratory exercise using Blackboard's Turnitin feature. Your Turnitin upload link is found on your Blackboard Course shell under the Laboratory folder.

***

For this exercise, you will need to use the package `mosaic` to find numerical and graphical summaries.



```r
# install package if necessary
if (!require(mosaic)) install.packages(`mosaic`)
# load the package in R
library(mosaic) # load the package mosaic to use its functions
```

1. The experimental data below contains food intake (in Kcal) for 15 men on the day following two nights of only 4 hours of sleep each night and for 15 mean on the day following two nights of 8 hours of sleep each each night. The mean participating in this experiment were randomly assigned to one of the two sleep conditions.


```r
four.hr.grp <- c(3585, 4470, 3068, 5338, 2221, 4791, 4435, 3099, 3187, 3901, 3868, 3869, 4878, 3632, 4518)  
eight.hr.grp <- c(4965, 3918, 1987, 4993, 5220, 3653, 3510, 3338, 4100, 5792, 4547, 3319, 4304, 4057)
```

  i) Compute the mean and standard deviation of the two groups. Comment on what you see.  
  ii) Create a boxplot and histogram (with a fitted normal density curve) for the food intake in the two groups. Is the normal distribution a reasonable assumption for the sodium intake in both classes?  
  iii) Carry out a two-sample t test with alpha = 0.05 to determine if there is a significant difference in mean food intake for the two different sleep conditions.  
  iv) State the results of your t-test. Can you make conclusive statement based on the information in your data? Why?    

### Code chunk

```r
# start your code
# i) Compute the mean and standard deviation of the two groups.
# Comment on what you see.  
cat("4 hour group\n")
```

```
## 4 hour group
```

```r
cat("mean: ")
```

```
## mean:
```

```r
mean(four.hr.grp)
```

```
## [1] 3924
```

```r
cat("standard deviation: ")
```

```
## standard deviation:
```

```r
sd(four.hr.grp)
```

```
## [1] 829.6681
```

```r
cat("8 hour group\n")
```

```
## 8 hour group
```

```r
cat("mean: ")
```

```
## mean:
```

```r
mean(eight.hr.grp)
```

```
## [1] 4121.643
```

```r
cat("standard deviation: ")
```

```
## standard deviation:
```

```r
sd(eight.hr.grp)
```

```
## [1] 966.2004
```

```r
cat("In the eight hour group the mean increases but so does the standard deviation")
```

```
## In the eight hour group the mean increases but so does the standard deviation
```

```r
# ii) Create a boxplot and histogram (with a fitted normal density curve)
# for the food intake in the two groups.
# Is the normal distribution a reasonable assumption for the sodium intake in both classes?
bwplot(four.hr.grp)
```

![](week10-Exercise_files/figure-latex/unnamed-chunk-3-1.pdf)<!-- --> 

```r
histogram(four.hr.grp, fit="normal")
```

![](week10-Exercise_files/figure-latex/unnamed-chunk-3-2.pdf)<!-- --> 

```r
bwplot(eight.hr.grp)
```

![](week10-Exercise_files/figure-latex/unnamed-chunk-3-3.pdf)<!-- --> 

```r
histogram(eight.hr.grp, fit="normal")
```

![](week10-Exercise_files/figure-latex/unnamed-chunk-3-4.pdf)<!-- --> 

```r
cat("normality assumptions is xxxxx since")
```

```
## normality assumptions is xxxxx since
```

```r
# iii) Carry out a two-sample t test with alpha = 0.05 to determine if there is a significant difference in mean food intake for the two different sleep conditions.
t.test(four.hr.grp,
       eight.hr.grp,
       var.equal = TRUE,
       alternative = "two.sided")
```

```
## 
## 	Two Sample t-test
## 
## data:  four.hr.grp and eight.hr.grp
## t = -0.59226, df = 27, p-value = 0.5586
## alternative hypothesis: true difference in means is not equal to 0
## 95 percent confidence interval:
##  -882.3543  487.0686
## sample estimates:
## mean of x mean of y 
##  3924.000  4121.643
```

```r
# iv) State the results of your t-test.
# Can you make conclusive statement based on the information in your data? Why?  
cat("The p-value is more than alpha, we can conclude that we failed to reject the the null hypothesis.\n Hence we cannot draw any conclusion about the alternative.")
```

```
## The p-value is more than alpha, we can conclude that we failed to reject the the null hypothesis.
##  Hence we cannot draw any conclusion about the alternative.
```

```r
# last R code line
```
  

2. Instructors in two nutrition education programs have their SNAP-Ed students keep diaries of what they eat for a week, and then calculate the daily sodium intake in milligrams.  Since the classes have received different nutrition education programs, they want to see if the mean sodium intake is the same for both classes. 

The data are displayed in the table below:


```r
sodium <- read.table(header = T, text ="
Instructor       Student  Sodium
'Brendon Small'  a        1200
'Brendon Small'  b        1400
'Brendon Small'  c        1350
'Brendon Small'  d         950
'Brendon Small'  e        1400
'Brendon Small'  f        1150
'Brendon Small'  g        1300
'Brendon Small'  h        1325
'Brendon Small'  i        1425
'Brendon Small'  j        1500
'Brendon Small'  k        1250
'Brendon Small'  l        1150
'Brendon Small'  m         950
'Brendon Small'  n        1150
'Brendon Small'  o        1600
'Brendon Small'  p        1300
'Brendon Small'  q        1050
'Brendon Small'  r        1300
'Brendon Small'  s        1700
'Brendon Small'  t        1300
'Coach McGuirk'  u        1100
'Coach McGuirk'  v        1200
'Coach McGuirk'  w        1250
'Coach McGuirk'  x        1050
'Coach McGuirk'  y        1200
'Coach McGuirk'  z        1250
'Coach McGuirk'  aa       1350
'Coach McGuirk'  ab       1350
'Coach McGuirk'  ac       1325
'Coach McGuirk'  ad       1525
'Coach McGuirk'  ae       1225
'Coach McGuirk'  af       1125
'Coach McGuirk'  ag       1000
'Coach McGuirk'  ah       1125
'Coach McGuirk'  ai       1400
'Coach McGuirk'  aj       1200
'Coach McGuirk'  ak       1150
'Coach McGuirk'  al       1400
'Coach McGuirk'  am       1500
'Coach McGuirk'  an       1200
")
```

  i) Compare the sodium intake between the two classes. Use the `favstats` function. Comment on what you see.  
  ii) Create a boxplot and histogram (with a fitted normal density curve) for the sodium intake in the two classes. Is the normal distribution a reasonable assumption for the sodium intake in both classes?  
  iii) Carry a two-sample t-test with alpha = 0.05 to determine if there is a significant difference in mean sodium intake for the two different classes.  
  iv) State the results of your t-test. Can you make conclusive statement based on the information in your data? Why?  
  

### Code chunk

```r
# start your code

# i) Compare the sodium intake between the two classes.
# Use the `favstats` function. Comment on what you see.
favstats(Sodium ~ Instructor, data = sodium)
```

```
##      Instructor  min      Q1 median   Q3  max    mean       sd  n missing
## 1 Brendon Small  950 1150.00 1300.0 1400 1700 1287.50 193.7341 20       0
## 2 Coach McGuirk 1000 1143.75 1212.5 1350 1525 1246.25 142.4123 20       0
```

```r
cat("The mean in Brendon Small is slightly larger than that of Coach McGuirk.\n Similarly the median is also larger for Brendon")
```

```
## The mean in Brendon Small is slightly larger than that of Coach McGuirk.
##  Similarly the median is also larger for Brendon
```

```r
# ii) Create a boxplot and histogram (with a fitted normal density curve) for the sodium intake in the two classes.
# Is the normal distribution a reasonable assumption for the sodium intake in both classes?
bwplot(Sodium ~ Instructor, data = sodium)
```

![](week10-Exercise_files/figure-latex/unnamed-chunk-5-1.pdf)<!-- --> 

```r
histogram( ~ Sodium | Instructor,  fit = "normal", data = sodium)
```

![](week10-Exercise_files/figure-latex/unnamed-chunk-5-2.pdf)<!-- --> 

```r
cat("No the normality distribution is not a reasonable assumption for the sodium intake in either classes.")
```

```
## No the normality distribution is not a reasonable assumption for the sodium intake in either classes.
```

```r
# iii) Carry a two-sample t-test with alpha = 0.05
# to determine if there is a significant difference in mean sodium intake for the two different classes.  
t.test(
  Sodium ~ Instructor,
  data = sodium,
  var = TRUE,
  alternative = "two.sided"
)
```

```
## 
## 	Two Sample t-test
## 
## data:  Sodium by Instructor
## t = 0.76722, df = 38, p-value = 0.4477
## alternative hypothesis: true difference in means between group Brendon Small and group Coach McGuirk is not equal to 0
## 95 percent confidence interval:
##  -67.59215 150.09215
## sample estimates:
## mean in group Brendon Small mean in group Coach McGuirk 
##                     1287.50                     1246.25
```

```r
# iv) State the results of your t-test.
# Can you make conclusive statement based on the information in your data? Why?  
cat("Since the p-value in the t test is greater than alpha.\n We do not have anough evidence to reject the null hypothesis that there is a significant difference in the mean sodium intake for the two different classes.")
```

```
## Since the p-value in the t test is greater than alpha.
##  We do not have anough evidence to reject the null hypothesis that there is a significant difference in the mean sodium intake for the two different classes.
```

```r
# last R code line
```
