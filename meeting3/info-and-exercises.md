Meeting 3: Data Transformation & Exploratory Data Analysis
================
August 12, 2021 from 7:00-8:30pm ET

## Chapters to Read

This week, we’ll be discussing:

-   Pipes
-   Data Transformation
-   Exploratory Data Analysis (EDA)

### Physical Book

If you’re reading the physical book, the chapters to read are:

| Physical book chapters           | Pages   |
|:---------------------------------|:--------|
| Ch. 14: Pipes                    | 261-268 |
| Ch. 3: Data Transformation       | 43-76   |
| Ch. 5: Exploratory Data Analysis | 81-110  |

### Online Book

If you’re reading the online book, the chapters to read are:

| Chapter                          | Link                                                    |
|:---------------------------------|:--------------------------------------------------------|
| Ch. 18: Pipes                    | <https://r4ds.had.co.nz/pipes.html>                     |
| Ch. 5: Data Transformation       | <https://r4ds.had.co.nz/transform.html>                 |
| Ch. 7: Exploratory Data Analysis | <https://r4ds.had.co.nz/exploratory-data-analysis.html> |

## Exercises

All exercises refer to the online book chapters. The book exercises and
online exercises may differ, so to make sure everyone is doing the same
exercises, please refer to the online book chapters.

-   Chapter 5: Section 5.2.4 \# 1 (odd-numbered sub-parts only), \# 2 -
    4
-   Chapter 5: Section 5.3.1 \# 1, 3, 4
-   Chapter 5: Section 5.4.1 \# 1 - 4
-   Chapter 5: Section 5.5.2 \# 1, 3, 5
-   Chapter 5: Section 5.6.7 \# 2 - 6
-   Chapter 5: Section 5.7.1 \# 2, 4, 6, 8
-   Chapter 7: Section 7.3.4 \# 2 - 4
-   Chapter 7: Section 7.4.1 \# 1, 2
-   Chapter 7: Section 7.5. Do the first 2 problems of each section
    7.5.1.1, 7.5.2.1, and 7.5.3.1
-   BONUS: Follow the style of [this
    tweet](https://twitter.com/hadleywickham/status/1359852563726819332?s=20)
    to “translate” some of your favorite song lyrics into
    {tidyverse}-style code

Exercises are reproduced below.

### Chapter 5 Exercises

Whenever flights are referred to, use the `nycflights13::flights` data
to answer the question.

#### Section 5.2.4 \# 1 (odd-numbered sub-parts only), \# 2 - 4

1.  Find all flights that

    1.  Had an arrival delay of two or more hours
    2.  ~~Flew to Houston (`IAH` or `HOU`)~~
    3.  Were operated by United, American, or Delta
    4.  ~~Departed in summer (July, August, and September)~~
    5.  Arrived more than two hours late, but didn’t leave late
    6.  ~~Were delayed by at least an hour, but made up over 30 minutes
        in flight~~
    7.  Departed between midnight and 6am (inclusive)

> Solution:

``` r
# Had an arrival delay of two or more hours
# Were operated by United, American, or Delta
# Arrived more than two hours late, but didn't leave late
# Departed between midnight and 6am (inclusive)
```

2.  Sort `flights` to find the flights with longest departure delays.
    Find the flights that left earliest.

> Solution:

3.  Sort `flights` to find the fastest (highest speed) flights. (Hint:
    try sorting by a calculation).

> Solution:

4.  Which flights travelled the farthest? Which travelled the shortest?

> Solution:

``` r
# Which flights travelled the farthest?
# Which travelled the shortest?
```

#### Section 5.3.1 \# 1, 3, 4

1.  How could you use arrange() to sort all missing values to the start?
    (Hint: use is.na()).

> Solution:

3.  Sort flights to find the fastest (highest speed) flights.

> Solution:

4.  Which flights travelled the farthest? Which travelled the shortest?

> Solution:

#### Section 5.4.1 \# 1 - 4

1.  Brainstorm as many ways as possible to select `dep_time`,
    `dep_delay`, `arr_time`, and `arr_delay` from `flights`.

> Solution:

2.  What happens if you include the name of a variable multiple times in
    a select() call?

> Solution:

3.  What does the any\_of() function do? Why might it be helpful in
    conjunction with this vector?

``` r
vars <- c("year", "month", "day", "dep_delay", "arr_delay")
```

> Solution:

4.  Does the result of running the following code surprise you? How do
    the select helpers deal with case by default? How can you change
    that default?

``` r
select(flights, contains("TIME"))
```

> Solution:

#### Section 5.5.2 \# 1, 3, 5

1.  Currently dep\_time and sched\_dep\_time are convenient to look at,
    but hard to compute with because they’re not really continuous
    numbers. Convert them to a more convenient representation of number
    of minutes since midnight.

> Solution:

3.  Compare dep\_time, sched\_dep\_time, and dep\_delay. How would you
    expect those three numbers to be related?

> Solution:

5.  What does 1:3 + 1:10 return? Why?

> Solution:

#### Section 5.6.7 \# 2 - 6

2.  Come up with another approach that will give you the same output as
    `not_cancelled %>% count(dest)` and
    `not_cancelled %>% count(tailnum, wt = distance)` (without using
    `count()`).

> Solution:

3.  Our definition of cancelled flights
    (`is.na(dep_delay) | is.na(arr_delay)` ) is slightly suboptimal.
    Why? Which is the most important column?

> Solution:

4.  Look at the number of cancelled flights per day. Is there a pattern?
    Is the proportion of cancelled flights related to the average delay?

> Solution:

5.  Which carrier has the worst delays? Challenge: can you disentangle
    the effects of bad airports vs. bad carriers? Why/why not? (Hint:
    think about
    `flights %>% group_by(carrier, dest) %>% summarise(n())`)

> Solution:

6.  What does the `sort` argument to `count()` do. When might you use
    it?

> Solution:

#### Section 5.7.1 \# 2, 4, 6, 8

2.  Which plane (tailnum) has the worst on-time record?

> Solution:

4.  For each destination, compute the total minutes of delay. For each
    flight, compute the proportion of the total delay for its
    destination.

> Solution:

6.  Look at each destination. Can you find flights that are suspiciously
    fast? (i.e. flights that represent a potential data entry error).
    Compute the air time of a flight relative to the shortest flight to
    that destination. Which flights were most delayed in the air?

> Solution:

8.  For each plane, count the number of flights before the first delay
    of greater than 1 hour.

> Solution:

### Chapter 7 Exercises

Unless otherwise noted, answer the questions using the `diamonds` data.

#### Section 7.3.4 \# 2 - 4

2.  Explore the distribution of `price`. Do you discover anything
    unusual or surprising? (Hint: Carefully think about the `binwidth`
    and make sure you try a wide range of values.)

> Solution:

3.  How many diamonds are 0.99 carat? How many are 1 carat? What do you
    think is the cause of the difference?

> Solution:

4.  Compare and contrast `coord_cartesian()` vs `xlim()` or `ylim()`
    when zooming in on a histogram. What happens if you leave binwidth
    unset? What happens if you try and zoom so only half a bar shows?

> Solution:

#### Section 7.4.1 \# 1, 2

1.  What happens to missing values in a histogram? What happens to
    missing values in a bar chart? Why is there a difference?

> Solution:

2.  What does `na.rm = TRUE` do in `mean()` and `sum()`?

> Solution:

#### Section 7.5. Do the first 2 problems of each section 7.5.1.1, 7.5.2.1, and 7.5.3.1

##### Section 7.5.1.1

1.  Use what you’ve learned to improve the visualisation of the
    departure times of cancelled vs. non-cancelled flights.

> Solution:

2.  What variable in the diamonds dataset is most important for
    predicting the price of a diamond? How is that variable correlated
    with cut? Why does the combination of those two relationships lead
    to lower quality diamonds being more expensive?

> Solution:

##### Section 7.5.2.1

1.  How could you rescale the count dataset above to more clearly show
    the distribution of cut within colour, or colour within cut?

> Solution:

2.  Use `geom_tile()` together with dplyr to explore how average flight
    delays vary by destination and month of year. What makes the plot
    difficult to read? How could you improve it?

> Solution:

##### Sedtion 7.5.3.1

1.  Instead of summarising the conditional distribution with a boxplot,
    you could use a frequency polygon. What do you need to consider when
    using `cut_width()` vs `cut_number()`? How does that impact a
    visualisation of the 2d distribution of `carat` and `price`?

> Solution:

2.  Visualise the distribution of carat, partitioned by price.

> Solution:

### Bonus Exercise

Follow the style of [this
tweet](https://twitter.com/hadleywickham/status/1359852563726819332?s=20)
to “translate” some of your favorite song lyrics into {tidyverse}-style
code

<img src="img/pipe_song_tweet.png" width="50%" style="display: block; margin: auto;" />
