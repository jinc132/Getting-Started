---
title: "Getting Stated with R"
author: "Jin Chang"
date: "1/14/2019"
output: html_document
---


#The Intro
This is *Jinc132*’s first assignment for **Geog458**. Our course page can be accessed here.

## LINK
[Here](https://canvas.uw.edu/courses/1269928)

## Image
![This is where I reside 70% of the time!](https://s3-us-west-2.amazonaws.com/uw-s3-cdn/wp-content/uploads/sites/98/2014/09/07214435/Signature_Stacked_Purple_Hex.png)

### Math
This is the _pythorean theorem_ : \[ x^n + y^n = z^n \]

### Table of Values

  Month      Days
----------  ------
 February     12
 March        13
 January      15
 May          23
 December     30
 April        14
[Math-Geeks]: https://en.wikipedia.org/wiki/Birthday

###Task 6

```r
library(rmarkdown)
```

```
## Warning: package 'rmarkdown' was built under R version 3.4.4
```

```r
100/10+2
```

```
## [1] 12
```

```r
100/(10+2)
```

```
## [1] 8.333333
```

```r
sqrt(140) * 40
```

```
## [1] 473.2864
```

```r
log10(1/3)
```

```
## [1] -0.4771213
```

```r
log(982) - 3
```

```
## [1] 3.889591
```
###Task 7

```r
p1 <- 3 * 5
p2 <- 3 / p1

log10(p1 + p2)
```

```
## [1] 1.181844
```

```r
p1^p2
```

```
## [1] 1.718772
```

```r
(p1 * 450) / (p2 / 30) ^(2/100)
```

```
## [1] 7461.491
```

### Task 8 

```r
val <- seq(1:30)
strings <- c("Mary","had","a","little","lamb")
length(val)
```

```
## [1] 30
```

```r
length(strings)
```

```
## [1] 5
```

```r
sum(val)
```

```
## [1] 465
```

```r
#sum(strings)
```

### Task 9

```r
num <- seq(1:5)
hiVal <- seq(6,10)
num + hiVal
```

```
## [1]  7  9 11 13 15
```

```r
vect3 <- num * hiVal
```

### Task 10

```r
combined <- c(num,hiVal)
matrix <- rbind(num,hiVal,vect3)
print(matrix)
```

```
##       [,1] [,2] [,3] [,4] [,5]
## num      1    2    3    4    5
## hiVal    6    7    8    9   10
## vect3    6   14   24   36   50
```

```r
df <- data.frame(matrix)
df
```

```
##       X1 X2 X3 X4 X5
## num    1  2  3  4  5
## hiVal  6  7  8  9 10
## vect3  6 14 24 36 50
```
##Loading the Data
This is how to load data into R and how to convert it.


```r
library(tidyverse)
```

```
## Warning: package 'tidyverse' was built under R version 3.4.2
```

```
## ── Attaching packages ────────────────────────────────── tidyverse 1.2.1 ──
```

```
## ✔ ggplot2 3.1.0     ✔ purrr   0.2.4
## ✔ tibble  1.4.2     ✔ dplyr   0.7.7
## ✔ tidyr   0.8.2     ✔ stringr 1.3.1
## ✔ readr   1.1.1     ✔ forcats 0.3.0
```

```
## Warning: package 'ggplot2' was built under R version 3.4.4
```

```
## Warning: package 'tibble' was built under R version 3.4.3
```

```
## Warning: package 'tidyr' was built under R version 3.4.4
```

```
## Warning: package 'purrr' was built under R version 3.4.2
```

```
## Warning: package 'dplyr' was built under R version 3.4.4
```

```
## Warning: package 'stringr' was built under R version 3.4.4
```

```
## Warning: package 'forcats' was built under R version 3.4.3
```

```
## ── Conflicts ───────────────────────────────────── tidyverse_conflicts() ──
## ✖ dplyr::filter() masks stats::filter()
## ✖ dplyr::lag()    masks stats::lag()
```

```r
file <- read.csv("China_EO_49to17.csv", fileEncoding = "latin1")
data <- as_tibble(file)

Year = seq(from=1949,to=2017)
data$Year = Year

obj1 <- data %>%
  arrange(desc(Year)) %>%
  filter(Year >= 2000) %>%
  select(c(),Shanghai_Enterprise, Shanghai_Output, Beijing_Enterprise, Beijing_Output)
```

```
## Warning: package 'bindrcpp' was built under R version 3.4.4
```

```r
obj1 
```

```
## # A tibble: 18 x 4
##    Shanghai_Enterprise Shanghai_Output Beijing_Enterprise Beijing_Output
##                  <int>           <dbl>              <int>          <dbl>
##  1                8122          36094.               3231            NA 
##  2                8351          31136.               3340         18087.
##  3                8994          31050.               3548         17450.
##  4                9469          32665.               3686         18453.
##  5                9796          32089.               3641         17371.
##  6                9772          31548.               3692         15596.
##  7                9962          32445.               3746         14514.
##  8               16684          30114.               6884         13700.
##  9               17906          24091.               6890         11039.
## 10               18792          25121.               7205         10413.
## 11               15099          22260.               6397          9648.
## 12               14404          18573.               6400          8210 
## 13               14809          15768.               6300          6946.
## 14               15766          12885.               6871          4881.
## 15               11098          10343.               4019          3810.
## 16               10057           7741.               4551          3173.
## 17                9762           7004.               4356          2909.
## 18                8574           6205.               4572          2565.
```

```r
ratios <- obj1 %>%
  mutate("Output_Ratio"= Beijing_Output/Shanghai_Output)

ratios
```

```
## # A tibble: 18 x 5
##    Shanghai_Enterp… Shanghai_Output Beijing_Enterpr… Beijing_Output
##               <int>           <dbl>            <int>          <dbl>
##  1             8122          36094.             3231            NA 
##  2             8351          31136.             3340         18087.
##  3             8994          31050.             3548         17450.
##  4             9469          32665.             3686         18453.
##  5             9796          32089.             3641         17371.
##  6             9772          31548.             3692         15596.
##  7             9962          32445.             3746         14514.
##  8            16684          30114.             6884         13700.
##  9            17906          24091.             6890         11039.
## 10            18792          25121.             7205         10413.
## 11            15099          22260.             6397          9648.
## 12            14404          18573.             6400          8210 
## 13            14809          15768.             6300          6946.
## 14            15766          12885.             6871          4881.
## 15            11098          10343.             4019          3810.
## 16            10057           7741.             4551          3173.
## 17             9762           7004.             4356          2909.
## 18             8574           6205.             4572          2565.
## # ... with 1 more variable: Output_Ratio <dbl>
```

