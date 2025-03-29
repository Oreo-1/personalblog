---
layout: post
title: "Introduction to R and Descriptive Statistic"
subtitle: "TIL there is a programming language specific to data science."
date: 2025-03-28
author: "oreo"
header-img: "assets/r.png"
tags: 
    - Statistics
---

# What in the world is R programming language?
The R programming language created by Ross Ihaka and Robert Gentleman in 1993 is an open-source language primarily used for statistical computing, data analysis, and graphical visualization. It's widely used by statisticians, data scientists, and researchers. And of course, a student who just got an assignment by their lecturer.

## How to install and use the R programming language
- First, head to the [CRAN website](https://cran.r-project.org/) and pick a version based on your current operating system
- Next, head to the [POSIT website](https://posit.co/downloads/) to grab RStudio, the recommended IDE for R. Alternatively, you can setup R in visual studio code by [following these steps.](https://code.visualstudio.com/docs/languages/r)
- To run an entire R script, click on the "Source" button or Ctrl-Shift-Enter. To run selected line, click "Run" or Ctrl-Enter

### Basic arithmetic operations in R
``` R
# ==========================================
# BASIC ARITHMETIC OPERATIONS IN R
# ==========================================

# 1. Addition (+)
5 + 3  # Output: 8

# 2. Subtraction (-)
10 - 4  # Output: 6

# 3. Multiplication (*)
6 * 7  # Output: 42

# 4. Division (/)
20 / 5  # Output: 4

# 5. Exponentiation (^ or **)
2 ^ 3   # Output: 8 (2 cubed)
3 ** 2  # Output: 9 (3 squared)

# 6. Modulus (Remainder, %%)
10 %% 3  # Output: 1 (10 ÷ 3 leaves remainder 1)

# 7. Integer Division (%/%)
10 %/% 3  # Output: 3 (3 fits fully into 10 three times)

# ==========================================
# USING VARIABLES
# ==========================================
x <- 15
y <- 4

sum <- x + y       # 15 + 4 = 19
difference <- x - y # 15 - 4 = 11
product <- x * y   # 15 * 4 = 60

cat("Sum:", sum, "\n")           # \n adds a newline
cat("Difference:", difference, "\n")
cat("Product:", product, "\n")

# ==========================================
# ORDER OF OPERATIONS (PEMDAS/BODMAS)
# ==========================================
(2 + 3) * 4   # Output: 20 (parentheses first)
2 + 3 * 4     # Output: 14 (multiplication before addition)

# ==========================================
# PRACTICAL EXAMPLE: AREA OF A CIRCLE
# ==========================================
radius <- 5
area <- pi * radius ^ 2  # pi is a built-in constant in R
cat("Area of circle with radius", radius, "=", area, "\n")  # Output: ~78.53982
```

### Importing a data in R
the R programming language can read many data formats (.csv, .tsv, .xlsx to name a few).
- for this assignment, I was given the task to find the mean, median, and modus from [nutrient.csv](https://online.stat.psu.edu/stat505/sites/stat505/files/lesson01/SP23%20Data/nutrient.csv)

``` R
data <- read.csv("path\\to\\file\\nutrient.csv") # reading the CSV file
head(data) # is used to get the first rows of the DataFrame, Vector, or compatible object

modus <- function(x) {
  uniq_x <- unique(x)
  uniq_x[which.max(tabulate(match(x, uniq_x)))]
}

print("Mean")
print(sapply(data, mean))

print("Median")
print(sapply(data, median))

print("Modus")
print(sapply(data, modus))
```
which outputs to
``` R
> data <- read.csv("C:\\Users\\USER\\Desktop\\Rprogramming\\nutrient.csv") # reading the CSV file

> head(data) # is used to get the first rows of the DataFrame, Vector, or compatible object
  id calcium   iron protein vitamin.A vitamin.C
1  1  522.29 10.188  42.561    349.13    54.141
2  2  343.32  4.113  67.793    266.99    24.839
3  3  858.26 13.741  59.933    667.90   155.455
4  4  575.98 13.245  42.215    792.23   224.688
5  5 1927.50 18.919 111.316    740.27    80.961
6  6  607.58  6.800  45.785    165.68    13.050

> modus <- function(x) {
+   uniq_x <- unique(x)
+   uniq_x[which.max(tabulate(match(x, uniq_x)))]
+ }

> print("Mean")
[1] "Mean"

> print(sapply(data, mean))
       id   calcium      iron   protein vitamin.A vitamin.C 
464.25645 624.04925  11.12990  65.80344 839.63535  78.92845 

> print("Median")
[1] "Median"

> print(sapply(data, median))
       id   calcium      iron   protein vitamin.A vitamin.C 
  457.000   548.290    10.033    61.072   524.030    53.594 

> print("Modus")
[1] "Modus"

> print(sapply(data, modus))
       id   calcium      iron   protein vitamin.A vitamin.C 
    1.000   522.290     8.950    89.235     0.000     0.000 
```
## Conclusion
I find R interesting. I didn't know a programming language for such a specific task to exist. I always thought the same could be done by something like Python which seems to be the jack-of-all-trades language these days. I've always been interested in statistics but this.. along with many other data-science related lecture only proves that I have much to learn.