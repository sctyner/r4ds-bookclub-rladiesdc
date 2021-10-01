Meeting 6:
================
Septemmber 23, 2021 from 7:00-8:30pm ET

## Chapters to Read

This week, we’ll be discussing:

-   Functions
-   Vectors
-   Iteration

### Physical Book

If you’re reading the physical book, the chapters to read are:

| Physical book chapters | Pages   |
|:-----------------------|:--------|
| Ch. 15: Functions      | 269-290 |
| Ch. 16: Vectors        | 291-312 |
| Ch. 17: Iteration      | 313-339 |

### Online Book

If you’re reading the online book, the chapters to read are:

| Chapter                            | Link                                        |
|:-----------------------------------|:--------------------------------------------|
| Ch. 17: Introduction (Programming) | <https://r4ds.had.co.nz/program-intro.html> |
| Ch. 19: Functions                  | <https://r4ds.had.co.nz/functions.html>     |
| Ch. 20: Vectors                    | <https://r4ds.had.co.nz/vectors.html>       |
| Ch. 21: Iteration                  | <https://r4ds.had.co.nz/iteration.html>     |

## Exercises

All exercises refer to the online book chapters. The book exercises and
online exercises may differ, so to make sure everyone is doing the same
exercises, please refer to the online book chapters.

-   Chapter 19: Section 19.2.1 \# 3, 4
-   Chapter 19: Section 19.3.1 \# 1
-   Chapter 19: Section 19.4.4 \# 3
-   Chapter 19: Section 19.5.5 \# 2
-   Chapter 20: Section 20.3.5 \# 5
-   Chapter 20: Section 20.4.6 \# 4 (all parts)
-   Chapter 20: Section 20.7.4 \# 1 - 3
-   Chapter 21: Section 21.2.1 \# 4
-   Chapter 21: Section 21.3.5 \# 3
-   Chapter 21: Section 21.5.3 \# 5
-   Chapter 21: Section 21.9.3 \# 1

Exercises are reproduced below.

### Chapter 19

#### Section 19.2.1 \# 3, 4

3.  Practice turning the following code snippets into functions. Think
    about what each function does. What would you call it? How many
    arguments does it need? Can you rewrite it to be more expressive or
    less duplicative?

    ``` r
    mean(is.na(x))
    x / sum(x, na.rm = TRUE)
    sd(x, na.rm = TRUE) / mean(x, na.rm = TRUE)
    ```

> Sam’s solution:

``` r
# mean(is.na(x))
perc_miss <- function(x){
  mean(is.na(x))
}
# x / sum(x, na.rm = TRUE)
stdz <- function(x){
  x / sum(x, na.rm = TRUE)
}
# sd(x, na.rm = TRUE) / mean(x, na.rm = TRUE)
cov <- function(x, narm){
  sd(x, na.rm = narm) / mean(x, na.rm = narm)
}
```

4.  Write your own functions to compute the variance and skewness of a
    numeric vector. Variance is defined as
    $$
    \\mathrm{Var}(x) = \\frac{1}{n - 1} \\sum\_{i=1}^n (x\_i - \\bar{x}) ^2 \\text{,}
    $$
    where $\\bar{x} = (\\sum\_i^n x\_i) / n$ is the sample mean.
    Skewness is defined as
    $$
    \\mathrm{Skew}(x) = \\frac{\\frac{1}{n-2}\\left(\\sum\_{i=1}^n(x\_i - \\bar x)^3\\right)}{\\mathrm{Var}(x)^{3/2}} \\text{.}
    $$

> Sam’s Solution:

``` r
my_var <- function(x){
  x <- na.omit(x)
  xbar <- mean(x)
  n <- length(x)
  
  sum((x - xbar)^2) * (1/(n-1))
  
}

my_skew <- function(x){
  x <- na.omit(x)
  xbar <- mean(x)
  n <- length(x)
  v <- my_var(x)
  
  (1/ (n-2)) * (sum((x-xbar)^3)) / (v^(3/2))
}
```

#### Section 19.3.1 \# 1

1.  Read the source code for each of the following three functions,
    puzzle out what they do, and then brainstorm better names.

    ``` r
    f1 <- function(string, prefix) {
      substr(string, 1, nchar(prefix)) == prefix
    }
    f2 <- function(x) {
      if (length(x) <= 1) return(NULL)
      x[-length(x)]
    }
    f3 <- function(x, y) {
      rep(y, length.out = length(x))
    }
    ```

> Sam’s solution:

``` r
# f1: takes a string and a prefix (both chars) and checks if the string
# has the prefix prefix. 
# new name: prefix_chk 

# f2: takes a vector and removes the last element unless it's a 0 or 1 length
# new name: rm_last

# f3: takes 2 values x, y and creates a vector of length x whose elements are
# all y. 
# new name: repeat_yx 
```

#### Section 19.4.4 \# 3

3.  Implement a `fizzbuzz` function. It takes a single number as input.
    If the number is divisible by three, it returns “fizz”. If it’s
    divisible by five it returns “buzz”. If it’s divisible by three and
    five, it returns “fizzbuzz”. Otherwise, it returns the number. Make
    sure you first write working code before you create the function.

> Christina’s solution:

``` r
fizzbuzz_fun <- function(x) {
  if (x %% 3 == 0) {
   message("fizz")
 } else if (x %% 5 == 0) {
   message("buzz")
 } else {
   message("fizzbuzz")
   }
}

fizzbuzz_fun(3)
fizzbuzz_fun(5)
fizzbuzz_fun(15)
# should return fizbuzz
fizzbuzz_fun(4)
# should return 4
```

``` r
fizzbuzz_fun <- function(x) {
  if (x %% 15 == 0){
    message("fizzbuzz")
  } else if (x %% 3 == 0) {
   message("fizz")
 } else if (x %% 5 == 0) {
   message("buzz")
 } else {
   message(as.character(x))
   }
}
fizzbuzz_fun(3)
fizzbuzz_fun(5)
fizzbuzz_fun(15)
# should return fizbuzz
fizzbuzz_fun(4)
# should return 4
```

> Ellen’s Solution:

``` r
fizzbuzz <- function (x) {
  if (x%%3 == 0 & x%%5 == 0) {
  print("fizzbuzz")
} else if (x%%3 == 0) {
  print("fizz")
} else if (x%%5 == 0) {
  print("buzz")
} else print(x)
}

fizzbuzz(3)
```

    ## [1] "fizz"

``` r
fizzbuzz(5)
```

    ## [1] "buzz"

``` r
fizzbuzz(15)
```

    ## [1] "fizzbuzz"

``` r
fizzbuzz(4)
```

    ## [1] 4

``` r
# should return 4
```

> Sam’s solution:

``` r
fizzbuzz <- Vectorize(function(x){
  if (!is.numeric(x) | length(x) > 1){
    stop("x must be a single number")
  }
  
  div3 <- x %% 3
  div5 <- x %% 5

  if (div3 == 0 & div5 == 0){
    return("fizzbuzz")
  } else if (div3 == 0){
    return("fizz")
  } else if (div5 == 0){
    return("buzz")
  } else {
    return(x)
  }
})

fizzbuzz(3)
```

    ## [1] "fizz"

``` r
fizzbuzz(1:30)
```

    ##  [1] "1"        "2"        "fizz"     "4"        "buzz"     "fizz"    
    ##  [7] "7"        "8"        "fizz"     "buzz"     "11"       "fizz"    
    ## [13] "13"       "14"       "fizzbuzz" "16"       "17"       "fizz"    
    ## [19] "19"       "buzz"     "fizz"     "22"       "23"       "fizz"    
    ## [25] "buzz"     "26"       "fizz"     "28"       "29"       "fizzbuzz"

#### Section 19.5.5 \# 2

2.  It’d be nice if you could supply multiple characters to the pad
    argument, e.g. `rule("Title", pad = "-+")`. Why doesn’t this
    currently work? How could you fix it?

From the text:

``` r
rule <- function(..., pad = "-") {
  title <- paste0(...)
  width <- getOption("width") - nchar(title) - 5
  cat(title, " ", stringr::str_dup(pad, width), "\n", sep = "")
}
rule("Important output")
```

    ## Important output -----------------------------------------------------------

``` r
rule("Title", pad = "-+")
```

    ## Title -+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+

> Sam’s Solution:

``` r
rule("Title", pad = "-+")
```

    ## Title -+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+

``` r
# result is too long 

rule2 <- function(..., pad = "-") {
  title <- paste0(...)
  width <- getOption("width") - nchar(title) - 5
  width2 <- floor(width / stringr::str_length(pad))
  cat(title, " ", stringr::str_dup(pad, width2), "\n", sep = "")
}
rule("Title", pad = "-+")
```

    ## Title -+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+

``` r
rule2("Title", pad = "-+")
```

    ## Title -+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+

``` r
rule2("Title", pad = "-+#")
```

    ## Title -+#-+#-+#-+#-+#-+#-+#-+#-+#-+#-+#-+#-+#-+#-+#-+#-+#-+#-+#-+#-+#-+#-+#

``` r
rule2("Here is A Really Really Long Title I Should Cut Down", pad = "-+")
```

    ## Here is A Really Really Long Title I Should Cut Down -+-+-+-+-+-+-+-+-+-+-+

``` r
rule2("Here is A Really Really Long Title I Should Cut Down", pad = "-+#")
```

    ## Here is A Really Really Long Title I Should Cut Down -+#-+#-+#-+#-+#-+#-+#

### Chapter 20

#### Section 20.3.5 \# 5

5.  What functions from the readr package allow you to turn a string
    into logical, integer, and double vector?

> Sam’s Solution:

``` r
readr::parse_logical(c("T", "F", "FALSE", "TRUE"))
```

    ## [1]  TRUE FALSE FALSE  TRUE

``` r
readr::parse_integer(c("1", "4", "1000", "100.1", "test1"))
```

    ## [1]    1    4 1000   NA   NA
    ## attr(,"problems")
    ## # A tibble: 2 × 4
    ##     row   col expected               actual
    ##   <int> <int> <chr>                  <chr> 
    ## 1     4    NA no trailing characters 100.1 
    ## 2     5    NA no trailing characters test1

``` r
readr::parse_double(c("1", "4", "1000", "100.1", "test1"))
```

    ## [1]    1.0    4.0 1000.0  100.1     NA
    ## attr(,"problems")
    ## # A tibble: 1 × 4
    ##     row   col expected actual
    ##   <int> <int> <chr>    <chr> 
    ## 1     5    NA a double test1

``` r
readr::parse_number(c("1", "4", "1000", "100.1", "test1"))
```

    ## [1]    1.0    4.0 1000.0  100.1    1.0

#### Section 20.4.6 \# 4 (all parts)

4.  Create functions that take a vector as input and return:

    1.  The last value. Should you use `[` or `[[`?
    2.  The elements at even numbered positions.
    3.  Every element except the last value.
    4.  Only even numbers (and no missing values).

> Live Solution:

``` r
# The elements at even numbered positions.
vec_even <- function(x){
  
  n <- length(x)
  
  idx <- 1:n %% 2 == 0
  
  x[idx]
  
}
x <- 1:10
vec_even(x)
```

    ## [1]  2  4  6  8 10

``` r
# Only even numbers (and no missing values).
vec_even2 <- function(x){
  
  x <- na.omit(x)
  
  idx <- x %% 2 == 0
  
  x[idx]
}
vec_even2(x)
```

    ## [1]  2  4  6  8 10

``` r
vec_even(c(2,3,4,NA))
```

    ## [1]  3 NA

``` r
vec_even2(c(2,3,NA,5))
```

    ## [1] 2

> Sam’s Solution:

``` r
# a.  The last value. Should you use `[` or `[[`?
vec_last <- function(x){
  n <- length(x)
  x[n]
}
# b.  The elements at even numbered positions.
vec_even <- function(x){
  n <- length(x)
  
  if (n <= 1) return(NULL)
  
  evens <- x %% 2 == 0
  
  x[evens]
  
}

# c.  Every element except the last value.
vec_chop <- function(x){
  n <- length(x)
  
  if (n <= 1) return(NULL)
  
  x[-n]
  
}
# d.  Only even numbers (and no missing values).
vec_even2 <- function(x){
  x <- na.omit(x)
  
  evens <- x %% 2 == 0
  
  x[evens]

}
```

#### Section 20.7.4 \# 1 - 3

1.  What does `hms::hms(3600)` return? How does it print? What primitive
    type is the augmented vector built on top of? What attributes does
    it use?

> Sam’s Solution:

``` r
res <- hms::hms(3600)
res
```

    ## 01:00:00

``` r
unclass(res)
```

    ## [1] 3600
    ## attr(,"units")
    ## [1] "secs"

``` r
typeof(res)
```

    ## [1] "double"

``` r
attributes(res)
```

    ## $units
    ## [1] "secs"
    ## 
    ## $class
    ## [1] "hms"      "difftime"

2.  Try and make a tibble that has columns with different lengths. What
    happens?

> Sam’s Solution:

``` r
tibble::tibble(x = 1:10, y = 2:10)
```

    ## Error: Tibble columns must have compatible sizes.
    ## * Size 10: Existing data.
    ## * Size 9: Column `y`.
    ## ℹ Only values of size one are recycled.

3.  Based on the definition above, is it ok to have a list as a column
    of a tibble?

> Sam’s Solution:

``` r
# yes, as long as it is the same length as the other columns: 
tibble::tibble(x = 1:10, xlist = list(1:10)) 
```

    ## # A tibble: 10 × 2
    ##        x xlist     
    ##    <int> <list>    
    ##  1     1 <int [10]>
    ##  2     2 <int [10]>
    ##  3     3 <int [10]>
    ##  4     4 <int [10]>
    ##  5     5 <int [10]>
    ##  6     6 <int [10]>
    ##  7     7 <int [10]>
    ##  8     8 <int [10]>
    ##  9     9 <int [10]>
    ## 10    10 <int [10]>

### Chapter 21

#### Section 21.2.1 \# 4

4.  It’s common to see for loops that don’t preallocate the output and
    instead increase the length of a vector at each step:

``` r
output <- vector("integer", 0)
for (i in seq_along(x)) {
  output <- c(output, lengths(x[[i]]))
}
output
```

How does this affect performance? Design and execute an experiment.

> Sam’s Solution:

``` r
# pre-allocated 
output <- vector("integer", 1000)
p <- Sys.time()
for (i in seq_along(output)){
  output[i] <- i
}
d1 <- Sys.time() - p

# not pre-allocated 
p <- Sys.time()
output <- vector("integer", 0)
for (i in 1:1000){
  output <- c(output, i)
}
d2 <- Sys.time() - p

as.numeric(d2)/as.numeric(d1)
```

    ## [1] 1.616862

``` r
# not pre-allocating is nearly 2x slower! 
```

#### Section 21.3.5 \# 3

3.  Write a function that prints the mean of each numeric column in a
    data frame, along with its name. For example, `show_mean(mpg)` would
    print:

    ``` r
    show_mean(mpg)
    #> displ:   3.47
    #> year: 2004
    #> cyl:     5.89
    #> cty:    16.86
    ```

    (Extra challenge: what function did I use to make sure that the
    numbers lined up nicely, even though the variable names had
    different lengths?)

> Sam’s Solution:

``` r
data(mpg, package = "ggplot2")

show_mean <- function(dat){
  dat %>% 
  select_if(is.numeric) %>% 
  summarize(across(everything(), mean, na.rm = T)) -> summ
  
  res <- vector("character", ncol(summ))
  for (i in seq_along(ncol(summ))){
  
    res <- str_c(names(summ), ":", " ", round(summ, 2), "\n")
  
  }

  cat(res)
  
}

show_mean(mpg)
```

    ## displ: 3.47
    ##  year: 2003.5
    ##  cyl: 5.89
    ##  cty: 16.86
    ##  hwy: 23.44

``` r
show_mean(iris)
```

    ## Sepal.Length: 5.84
    ##  Sepal.Width: 3.06
    ##  Petal.Length: 3.76
    ##  Petal.Width: 1.2

> Live solution:

``` r
iris2 <- select_if(iris, is.numeric)

nm <- names(iris2)
nm <- str_c(nm, ":")
nm_len <- max(str_length(nm))

means <- vector("double", ncol(iris2))
for ( i in 1:ncol(iris2)){
  means[i] <- mean(iris2[[i]], na.rm = T)
}
means <- round(means, 2)


nm <- format(nm)
means <- format(means)
str_c("\n", nm, means, sep = " ") %>% 
  cat()
```

    ## 
    ##  Sepal.Length: 5.84 
    ##  Sepal.Width:  3.06 
    ##  Petal.Length: 3.76 
    ##  Petal.Width:  1.20

``` r
show_mean <- function(dat){
  dat <- select_if(dat, is.numeric)
  
  nm <- names(dat)
  nm <- str_c(nm, ":")
  
  N <- ncol(dat)
  
  means <- vector("double", N)
  for ( i in 1:N){
    means[i] <- mean(dat[[i]], na.rm = T)
  }
  means <- round(means, 2)
  nm <- format(nm)
  means <- format(means)
  
  str_c("\n", nm, means, sep = " ") %>% 
    cat()

}
```

#### Section 21.5.3 \# 5

5.  Rewrite `map(x, function(df) lm(mpg ~ wt, data = df))` to eliminate
    the anonymous function.

> Sam’s Solution:

``` r
map(mpg,  function(.) lm(mpg ~ wt, data = .))
```

    ## Error in model.frame.default(formula = mpg ~ wt, data = ., drop.unused.levels = TRUE): 'data' must be a data.frame, environment, or list

``` r
# hmmm what the heck was this function supposed to be? 
# looks like we're trying to fit a model to some sets of data. 
```

``` r
# here's what happened earlier in the book: 
models <- mtcars %>% 
  split(.$cyl) %>% 
  map(function(df) lm(mpg ~ wt, data = df))
models
```

    ## $`4`
    ## 
    ## Call:
    ## lm(formula = mpg ~ wt, data = df)
    ## 
    ## Coefficients:
    ## (Intercept)           wt  
    ##      39.571       -5.647  
    ## 
    ## 
    ## $`6`
    ## 
    ## Call:
    ## lm(formula = mpg ~ wt, data = df)
    ## 
    ## Coefficients:
    ## (Intercept)           wt  
    ##       28.41        -2.78  
    ## 
    ## 
    ## $`8`
    ## 
    ## Call:
    ## lm(formula = mpg ~ wt, data = df)
    ## 
    ## Coefficients:
    ## (Intercept)           wt  
    ##      23.868       -2.192

``` r
models <- mtcars %>% 
  split(.$cyl) %>% 
  map(~lm(mpg ~ wt, data = .))
models
```

    ## $`4`
    ## 
    ## Call:
    ## lm(formula = mpg ~ wt, data = .)
    ## 
    ## Coefficients:
    ## (Intercept)           wt  
    ##      39.571       -5.647  
    ## 
    ## 
    ## $`6`
    ## 
    ## Call:
    ## lm(formula = mpg ~ wt, data = .)
    ## 
    ## Coefficients:
    ## (Intercept)           wt  
    ##       28.41        -2.78  
    ## 
    ## 
    ## $`8`
    ## 
    ## Call:
    ## lm(formula = mpg ~ wt, data = .)
    ## 
    ## Coefficients:
    ## (Intercept)           wt  
    ##      23.868       -2.192

#### Section 21.9.3 \# 1

1.  Implement your own version of `every()` using a for loop. Compare it
    with `purrr::every()`. What does purrr’s version do that your
    version doesn’t?

> Sam’s solution

``` r
# purrr::every() checks that every element satisfies a predicate (i.e. do a check and return TRUE)

my_every <- function(x, fn){
  N <- length(x)
  check <- logical(N)
  for (i in 1:N){
    check[i] <- do.call(fn, x[i])
  }
  
  if (sum(check) == N){
    return(TRUE)
  } else {
    return(FALSE)
  }
}

x <- list("hello", 1, 1L, as.factor("goodbye"))
my_every(x, fn = is.numeric)
```

    ## [1] FALSE

``` r
every(x, is.numeric)
```

    ## [1] FALSE

The `purrr::every()` function can take arguments passed through the
`...` to the predicate function.

### Open Discussion

``` r
x <- 1:100
rng <- range(x, na.rm = TRUE)
# (x - rng[1]) / (rng[2] - rng[1])
```

### 19.4.4 \#4

How could you use cut() to simplify this set of nested if-else
statements?

``` r
if (temp <= 0) {
  "freezing"
} else if (temp <= 10) {
  "cold"
} else if (temp <= 20) {
  "cool"
} else if (temp <= 30) {
  "warm"
} else {
  "hot"
}
```

> Live solution:

``` r
temp <- -10:100

cut(temp, breaks = c(-Inf,0, 10, 20, 30, Inf), 
    labels = c("freezing", "cold", "cool", "warm", "hot"),
    right = T)
```

    ##   [1] freezing freezing freezing freezing freezing freezing freezing freezing
    ##   [9] freezing freezing freezing cold     cold     cold     cold     cold    
    ##  [17] cold     cold     cold     cold     cold     cool     cool     cool    
    ##  [25] cool     cool     cool     cool     cool     cool     cool     warm    
    ##  [33] warm     warm     warm     warm     warm     warm     warm     warm    
    ##  [41] warm     hot      hot      hot      hot      hot      hot      hot     
    ##  [49] hot      hot      hot      hot      hot      hot      hot      hot     
    ##  [57] hot      hot      hot      hot      hot      hot      hot      hot     
    ##  [65] hot      hot      hot      hot      hot      hot      hot      hot     
    ##  [73] hot      hot      hot      hot      hot      hot      hot      hot     
    ##  [81] hot      hot      hot      hot      hot      hot      hot      hot     
    ##  [89] hot      hot      hot      hot      hot      hot      hot      hot     
    ##  [97] hot      hot      hot      hot      hot      hot      hot      hot     
    ## [105] hot      hot      hot      hot      hot      hot      hot     
    ## Levels: freezing cold cool warm hot

``` r
cut(temp, breaks = c(min(temp),0, 10, 20, 30, max(temp)))
```

    ##   [1] <NA>     (-10,0]  (-10,0]  (-10,0]  (-10,0]  (-10,0]  (-10,0]  (-10,0] 
    ##   [9] (-10,0]  (-10,0]  (-10,0]  (0,10]   (0,10]   (0,10]   (0,10]   (0,10]  
    ##  [17] (0,10]   (0,10]   (0,10]   (0,10]   (0,10]   (10,20]  (10,20]  (10,20] 
    ##  [25] (10,20]  (10,20]  (10,20]  (10,20]  (10,20]  (10,20]  (10,20]  (20,30] 
    ##  [33] (20,30]  (20,30]  (20,30]  (20,30]  (20,30]  (20,30]  (20,30]  (20,30] 
    ##  [41] (20,30]  (30,100] (30,100] (30,100] (30,100] (30,100] (30,100] (30,100]
    ##  [49] (30,100] (30,100] (30,100] (30,100] (30,100] (30,100] (30,100] (30,100]
    ##  [57] (30,100] (30,100] (30,100] (30,100] (30,100] (30,100] (30,100] (30,100]
    ##  [65] (30,100] (30,100] (30,100] (30,100] (30,100] (30,100] (30,100] (30,100]
    ##  [73] (30,100] (30,100] (30,100] (30,100] (30,100] (30,100] (30,100] (30,100]
    ##  [81] (30,100] (30,100] (30,100] (30,100] (30,100] (30,100] (30,100] (30,100]
    ##  [89] (30,100] (30,100] (30,100] (30,100] (30,100] (30,100] (30,100] (30,100]
    ##  [97] (30,100] (30,100] (30,100] (30,100] (30,100] (30,100] (30,100] (30,100]
    ## [105] (30,100] (30,100] (30,100] (30,100] (30,100] (30,100] (30,100]
    ## Levels: (-10,0] (0,10] (10,20] (20,30] (30,100]

### Tibbles

``` r
tb <- tibble::tibble(x = 1:5, y = 5:1)
li <- list(1 , 2, 3,4)
li[[1]]
```

    ## [1] 1

``` r
li[1]
```

    ## [[1]]
    ## [1] 1

``` r
tb[[1]]
```

    ## [1] 1 2 3 4 5

``` r
tb[1]
```

    ## # A tibble: 5 × 1
    ##       x
    ##   <int>
    ## 1     1
    ## 2     2
    ## 3     3
    ## 4     4
    ## 5     5
