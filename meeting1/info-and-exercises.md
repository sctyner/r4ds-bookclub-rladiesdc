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

Exercises are reproduced below

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

2.  Tweak each of the following R commands so that they run correctly:

    ``` r
    libary(tidyverse)
    ggplot(dota = mpg) + 
      geom_point(maping = aes(x = displ, y = hwy))
    ```

3.  Press Alt + Shift + K. What happens? How can you get to the same
    place using the menus?

### Chapter 6 Exercises

1.  Go to the RStudio Tips Twitter account,
    <https://twitter.com/rstudiotips> and find one tip that looks
    interesting. Practice using it!

2.  What other common mistakes will RStudio diagnostics report? Read
    <https://support.rstudio.com/hc/en-us/articles/205753617-Code-Diagnostics>
    to find out.
