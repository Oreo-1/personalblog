---
layout: post
title: "Descriptive Statistics"
subtitle: "Understanding measures in descriptive statistics"
date: 2025-03-27
author: "oreo"
header-img: "assets/statisticmemeidk.webp"
header-mask: 0.7
mathjax: true
tags: 
    - Statistics
---

# What is Descriptive Statistics?
- Descriptive statistics is a type of statistics that deals with summarizing and arranging data to make it easier to understand. It includes measures like mean, median, and mode to describe the central tendency of data, and measures like range, variance, and standard deviation to ascertain variability. Data representation tools like histograms, box plots, and scatter plots also help to comprehend data patterns and distributions.
- Unlike inferential statistics, which forecasts or makes predictions about a population, descriptive statistics only provides a snapshot of the data and helps to determine trends, patterns, and outliers in a given dataset.

# Measures of Central Tendency
Descriptive statistics summarize and describe the main features of a dataset. They provide insights into the distribution, center, and spread of data. One fundamental aspect of descriptive statistics is **central tendency** which indicates the center of the data through measures like mean, median and mode, with each comes with it's own strengths and weaknesses:
1. **Mean –** The sum of all values divided by the total number of values.
    - Pros:
        - Uses all data points – Reflects every value in the dataset.
        - Mathematically powerful – Used in advanced statistics (e.g., regression, variance).
        - Precise – Provides a single, exact value for comparison.
    - Cons:
        - Sensitive to outliers – Extreme values skew the mean (e.g., billionaires distorting average income).
        - Misleading for skewed data – Not representative if data is highly uneven.
        - Requires numeric data – Can’t be used for categorical variables (e.g., colors, brands).
1. **Median –** The middle value when data is arranged in ascending or descending order.
    - Pros:
        - Robust to outliers – Unaffected by extreme values.
        - Works for skewed data – Better for income, housing prices, etc.
        - Ordinal data friendly – Can be used for ranked data (e.g., survey ratings).
    - Cons:
        - Ignores most values – Only considers the middle position, not magnitudes.
        - Less precise – Doesn’t account for the spread of data.
        - Harder to calculate for large datasets – Requires sorting data first.
1. **Mode –** The most frequently occurring value in a dataset.
    - Pros:
        - Works for any data type – Numeric, categorical, or ordinal (e.g., "most common car color").
        - Identifies peaks – Reveals clusters or common categories.
        - Unaffected by outliers – Only depends on frequency.
    - Cons:
        - May not exist – No mode if all values are unique (e.g., [1, 2, 3, 4]).
        - Can be misleading – Multiple modes (bimodal/multimodal) complicate interpretation.
        - Ignores most data – Only cares about frequency, not other values.

Technically, they all measures the "average" of the distribution (which confuses me for a good bit) though, the best one to use in a given situation depends on context and the type of variable given.

## Central Tendency Example
Say, these are the weight of luggage presented by airline passengers at the check-in (measured to the nearest kg).

$
18, 23, 20, 21, 24, 23, 20, 20, 15, 19, 24
$

### 1. **Mean (Arithmetic Average)**
The mean is calculated as:

$
\text{Mean} = \frac{\sum X_i}{N}
$

$
= \frac{18 + 23 + 20 + 21 + 24 + 23 + 20 + 20 + 15 + 19 + 24}{11}
$

$   
= \frac{227}{11} \approx 20.64
$

For our dataset:

$
\mu = \frac{18 + 23 + 20 + 21 + 24 + 23 + 20 + 20 + 15 + 19 + 24}{11} = \frac{227}{11} \approx 20.64
$

### 2. **Median (Middle Value)**
The median is the middle value when data is arranged in ascending order:

$
15, 18, 19, 20, 20, 20, 21, 23, 23, 24, 24
$

Since we have **11 numbers (odd count)**, the median is the 6th value:

$
\text{Median} = 20
$

### 3. **Mode (Most Frequent Value)**
The mode is the most frequently occurring number(s) in the dataset.

- The number **20** appears **3 times**.
- The numbers **23** and **24** appear **twice**.
- Other numbers appear only once.

Thus, the **mode is 20** (the most frequent value).

# Measures of Dispersion
Measures of dispersion describe how **spread out** or **varied** a dataset is. They complement measures of central tendency by indicating whether data points are tightly clustered or widely scattered. It's used to measure the amount of variation of a data set and tells us about its reliability and consistency; The higher the dispersion, the more variability there is, and the lower the dispersion, the more closely the data points cluster together.

Some of the common measures of dispersion are range, which is the difference between the highest and lowest values; variance, which is a measure of the average squared deviation from the mean; and standard deviation, which is the average distance of data points from the mean.

## Dispersion Example

### 1. **Range**
The **range** is the simplest measure of dispersion, representing the difference between the largest and smallest values in a dataset. It's calculated as:

$\text{Range = Maximum Value = Minimum Value}$

- Example:
    - For the dataset: [4, 7, 2, 9, 5]
    - Maximum = 9  
    - Minimum = 2  
    - Range = 9 - 2 = 7

### 2. **Variance**
**Variance** measures how far each data point is from the mean (average) of the dataset. It quantifies the average squared deviation from the mean. It has two formulas:
- **Population Variance** (for entire dataset): 

    $\sigma^2 = \frac{1}{N} \sum_{i=1}^{N} (x_i - \mu)^2$

    Where:
    - $\sigma^2$ = population variance  
    - $N$ = number of observations  
    - $x_i$ = each individual value  
    - $\mu$ = population mean

and

- **Sample Variance** (for a sample of the dataset):

    $s^2 = \frac{1}{n - 1} \sum_{i=1}^{n} (x_i - \bar{x})^2$

    Where:  
    - $s^2$ = sample variance  
    - $n$ = number of sample observations  
    - $x_i$ = each sample value  
    - $\bar{x}$ = sample mean

Example:
For the dataset: [4, 7, 2, 9, 5]  
Mean:

$
\mu = \frac{4 + 7 + 2 + 9 + 5}{5} = 5.4
$

Squared deviations:

$
(4 - 5.4)^2 = 1.96
$

$
(7 - 5.4)^2 = 2.56
$

$
(2 - 5.4)^2 = 11.56
$

$
(9 - 5.4)^2 = 12.96
$

$
(5 - 5.4)^2 = 0.16
$

Variance:

$
\sigma^2 = \frac{1.96 + 2.56 + 11.56 + 12.96 + 0.16}{5} = 5.84
$

### 3. **Standard Deviation**
**Standard deviation** is the square root of the variance, providing a measure of dispersion in the same units as the original data.

$\sigma = \sqrt{\sigma^2}$

Sample Standard Deviation:

$s = \sqrt{s^2}$

- Example:

    Using the variance from above:

    $\sigma^2 = 5.84$

    Then the population standard deviation is:

    $\sigma = \sqrt{5.84} \approx 2.42$

# Materials
## Videos to Watch:
<iframe width="560" height="315" src="https://www.youtube.com/embed/SplCk-t1BeA?si=c9Jpajf6LSpkmI92" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## Given Material: [Introduction to descriptive statistics](https://www.sydney.edu.au/content/dam/students/documents/mathematics-learning-centre/introduction-to-descriptive-statistics.pdf)