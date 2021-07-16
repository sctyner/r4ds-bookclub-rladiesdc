Meeting 1: Introductions to one another and to R & RStudio
================
July 15, 2021 from 7:00-8:30pm ET

## Chapters to Read

This week, we’ll be discussing:

-   Preface/Introduction
-   Workflow basics
-   Workflow scripts
-   Workflow projects

### Physical Book

If you’re reading the physical book, the chapters to read are:

| Physical book chapters   | Pages     |
|:-------------------------|:----------|
| Preface                  | ix - xxiv |
| Ch. 2: Workflow Basics   | 37-42     |
| Ch. 4: Workflow Scripts  | 77-79     |
| Ch. 6: Workflow Projects | 111-116   |

### Online Book

If you’re reading the online book, the chapters to read are:

| Chapter                   | Link                                            |
|:--------------------------|:------------------------------------------------|
| Welcome                   | <https://r4ds.had.co.nz/index.html>             |
| Ch 1: Introduction        | <https://r4ds.had.co.nz/introduction.html>      |
| Ch. 4: Workflow: basics   | <https://r4ds.had.co.nz/workflow-basics.html>   |
| Ch. 6: Workflow: scripts  | <https://r4ds.had.co.nz/workflow-scripts.html>  |
| Ch. 8: Workflow: projects | <https://r4ds.had.co.nz/workflow-projects.html> |

## Exercises

All exercises refer to the online book chapters. The book exercises and
online exercises may differ, so to make sure everyone is doing the same
exercises, please refer to the online book chapters.

-   Chapter 4: Section 4.4 \#1-3
-   Chapter 6: Section 6.3 \#1-2

Exercises are reproduced below.

### Chapter 4 Exercises

1.  Why does this code not work?

    ``` r
    my_variable <- 10
    my_varıable
    ```

        ## Error in eval(expr, envir, enclos): object 'my_varıable' not found

    Look carefully! (This may seem like an exercise in pointlessness,
    but training your brain to notice even the tiniest difference will
    pay off when programming.)

> The code doesn’t work because the `i` in `my_variable` was replaced
> with a `ı`, a different character. The lesson here is that R takes
> everything you do very literally: `my_variable` is totally different
> from `my_varıable` or `My_variable` in R’s eyes.

1.  Tweak each of the following R commands so that they run correctly:

    ``` r
    libary(tidyverse)
    ggplot(dota = mpg) + 
      geom_point(maping = aes(x = displ, y = hwy))

    fliter(mpg, cyl = 8)
    filter(diamond, carat > 3)
    ```

``` r
library(tidyverse)  # library not libary
ggplot(data = mpg) +  # data not dota
  geom_point(mapping = aes(x = displ, y = hwy))  # mapping not maping
```

<div class="figure" style="text-align: center">

<img src="info-and-exercises_files/figure-gfm/unnamed-chunk-5-1.png" alt="A plot of displ by highway mpg"  />
<p class="caption">
A plot of displ by highway mpg
</p>

</div>

``` r
filter(mpg, cyl == 8)  # filter not fliter, == not =
```

    ## # A tibble: 70 x 11
    ##    manufacturer model     displ  year   cyl trans  drv     cty   hwy fl    class
    ##    <chr>        <chr>     <dbl> <int> <int> <chr>  <chr> <int> <int> <chr> <chr>
    ##  1 audi         a6 quatt…   4.2  2008     8 auto(… 4        16    23 p     mids…
    ##  2 chevrolet    c1500 su…   5.3  2008     8 auto(… r        14    20 r     suv  
    ##  3 chevrolet    c1500 su…   5.3  2008     8 auto(… r        11    15 e     suv  
    ##  4 chevrolet    c1500 su…   5.3  2008     8 auto(… r        14    20 r     suv  
    ##  5 chevrolet    c1500 su…   5.7  1999     8 auto(… r        13    17 r     suv  
    ##  6 chevrolet    c1500 su…   6    2008     8 auto(… r        12    17 r     suv  
    ##  7 chevrolet    corvette    5.7  1999     8 manua… r        16    26 p     2sea…
    ##  8 chevrolet    corvette    5.7  1999     8 auto(… r        15    23 p     2sea…
    ##  9 chevrolet    corvette    6.2  2008     8 manua… r        16    26 p     2sea…
    ## 10 chevrolet    corvette    6.2  2008     8 auto(… r        15    25 p     2sea…
    ## # … with 60 more rows

``` r
filter(diamonds, carat > 3) # diamonds, not diamond, is an available dataset 
```

    ## # A tibble: 32 x 10
    ##    carat cut     color clarity depth table price     x     y     z
    ##    <dbl> <ord>   <ord> <ord>   <dbl> <dbl> <int> <dbl> <dbl> <dbl>
    ##  1  3.01 Premium I     I1       62.7    58  8040  9.1   8.97  5.67
    ##  2  3.11 Fair    J     I1       65.9    57  9823  9.15  9.02  5.98
    ##  3  3.01 Premium F     I1       62.2    56  9925  9.24  9.13  5.73
    ##  4  3.05 Premium E     I1       60.9    58 10453  9.26  9.25  5.66
    ##  5  3.02 Fair    I     I1       65.2    56 10577  9.11  9.02  5.91
    ##  6  3.01 Fair    H     I1       56.1    62 10761  9.54  9.38  5.31
    ##  7  3.65 Fair    H     I1       67.1    53 11668  9.53  9.48  6.38
    ##  8  3.24 Premium H     I1       62.1    58 12300  9.44  9.4   5.85
    ##  9  3.22 Ideal   I     I1       62.6    55 12545  9.49  9.42  5.92
    ## 10  3.5  Ideal   H     I1       62.8    57 12587  9.65  9.59  6.03
    ## # … with 22 more rows

> To find data sets in your environment: `data()` and hit Tab key inside
> of parens to look for all the data sets R has access to.

1.  Press Alt + Shift + K. What happens?

> Open up the keyboard shortcuts!

How can you get to the same place using the menus?

> Go to Tools (or Help) -&gt; Keyboard Shortcuts Help

### Chapter 6 Exercises

1.  Go to the RStudio Tips Twitter account,
    <https://twitter.com/rstudiotips> and find one tip that looks
    interesting. Practice using it!
    -   *Maddie:* “The”reflow" command Ctrl+Shift+/ of @RStudio never
        ceases to amaze me. Sometimes I scramble the docs on purpose,
        just to watch it bounce back perfectly! Is there a way to reflow
        the Description field of DESCRIPTION similarly? \#rstats"

    -   *Jill:* “I learned CTRL + SHIFT + M —&gt; %&gt;%”

    -   *Simon:* Ctrl + Enter to run the line in editor, no selecting
        needed

    -   *Anna:* CTRL + U at the end of a line deletes all of the code
        from that line; Also, CTRL + ALT + i makes a new code chunk in
        an rmarkdown.

    -   *Sam S:* [Visual markdown
        editor.](https://twitter.com/scarface_08944/status/1370352809275711490)
        (Rstudio version 1.4 or greater)

    -   *Neelima:* Ctrl+1 2 3 etc moves cursor between panes in RStudio

    -   *Paola:* Tweet from @ChelseaParlett. “In case you didn’t know
        the shortcut: highlighting multiple lines in \#rStudio and
        hitting tab to indent and Shift + tab to unindent MULTIPLE LINES
        AT ONCE I always do this when coding in python, but just never
        knew the command to do it in Rstudio!!”

    -   *Sam T:* Alt(option) + Click & Drag highlights lines
        independently; Spellcheck : Edit -&gt; Check spelling
2.  What other common mistakes will RStudio diagnostics report? Read
    <https://support.rstudio.com/hc/en-us/articles/205753617-Code-Diagnostics>
    to find out.
    -   *Jill:*
        -   Magic comments
        -   Proper R style: space padding.

``` r
ggplot(mpg) + 
  geom_point(aes(x = model, y = displ))

# not 

ggplot(mpg)+geom_point(aes(x=model,y=displ))
```

## Open Disussion

### What’s the deal with the Rmd code chunk and its arguments??

#### Backticks, braces and how to use:

-   No brackets after a set of backticks gets you verbatim text:

<!-- -->

    verbatim code

-   Define the engine in first argument after opening bracket, second
    argument is chunk name. Other arguments go after a comma after the
    name (see examples in source)

#### Code Chunk Arguments

-   See Yihui’s post: <https://yihui.org/knitr/options/>
-   Common ones (examples in source of this document):
    -   `eval`: **eval**uate/run the code or not?
    -   `echo`: display the code in the knitted document or not?
    -   `fig.align`: how to **align** **fig**ures resulting from code?
        (left, right, center)
    -   `fig.cap`: Add a **cap**tion to a **fig**ure

#### How to use RStudio Cloud as a single user?

-   RStudio Cloud: A totally online version of RStudio, no downloading
    required. For more info see:
    -   <https://rstudio.cloud/personal/about>
    -   <https://rstudio.cloud/learn/guide>
