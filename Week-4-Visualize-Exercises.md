# Visualize Data
Michael Torrisi
2025-02-13

- [Your Turn 0](#your-turn-0)
- [Your Turn 1](#your-turn-1)
- [Your Turn 2](#your-turn-2)
- [Your Turn 3](#your-turn-3)
- [Your Turn 4](#your-turn-4)
- [Your Turn 5](#your-turn-5)
- [Help Me](#help-me)
- [Your Turn 6](#your-turn-6)
- [Quiz](#quiz)
- [Take aways](#take-aways)

## Your Turn 0

Add a setup chunk that loads the tidyverse packages.

<details class="code-fold">
<summary>Code</summary>

``` r
head(mpg)
```

</details>

    # A tibble: 6 × 11
      manufacturer model displ  year   cyl trans      drv     cty   hwy fl    class 
      <chr>        <chr> <dbl> <int> <int> <chr>      <chr> <int> <int> <chr> <chr> 
    1 audi         a4      1.8  1999     4 auto(l5)   f        18    29 p     compa…
    2 audi         a4      1.8  1999     4 manual(m5) f        21    29 p     compa…
    3 audi         a4      2    2008     4 manual(m6) f        20    31 p     compa…
    4 audi         a4      2    2008     4 auto(av)   f        21    30 p     compa…
    5 audi         a4      2.8  1999     6 auto(l5)   f        16    26 p     compa…
    6 audi         a4      2.8  1999     6 manual(m5) f        18    26 p     compa…

## Your Turn 1

Run the code on the slide to make a graph. Pay strict attention to
spelling, capitalization, and parentheses!

<details class="code-fold">
<summary>Code</summary>

``` r
# Creates scatterplot with in-built mpg dataset
ggplot(mpg) + 
  geom_point(aes(x = displ,
                 y = hwy))
```

</details>

![](Week-4-Visualize-Exercises_files/figure-commonmark/First%20Visualization%20-%20Scatterplot-1.png)

## Your Turn 2

Replace this scatterplot with one that draws boxplots. Use the
cheatsheet. Try your best guess.

<details class="code-fold">
<summary>Code</summary>

``` r
# Creates boxplot with in-built mpg dataset
ggplot(data = mpg) +
  geom_boxplot(aes(x = class,
                   y = hwy))
```

</details>

![](Week-4-Visualize-Exercises_files/figure-commonmark/Second%20Visualization%20-%20Boxplot-1.png)

## Your Turn 3

Make a histogram of the `hwy` variable from `mpg`. Hint: do not supply a
y variable.

<details class="code-fold">
<summary>Code</summary>

``` r
# Creates histogram with in-built mpg dataset
ggplot(data = mpg) +
  geom_histogram(aes(x = hwy))
```

</details>

    `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](Week-4-Visualize-Exercises_files/figure-commonmark/Third%20Visualization%20-%20Histogram-1.png)

## Your Turn 4

Use the help page for `geom_histogram` to make the bins 2 units wide.

<details class="code-fold">
<summary>Code</summary>

``` r
# Creates histogram with in-built mpg dataset, and controls binwidth.
ggplot(data = mpg) +
  geom_histogram(aes(x = hwy),
                 binwidth = 2) + 
  labs(x = "Highway Mileage (mpg)",
       y = "Frequency")
```

</details>

![](Week-4-Visualize-Exercises_files/figure-commonmark/Fourth%20Visualization%20-%20Histogram%20with%20Binwidth-1.png)

## Your Turn 5

Add `color`, `size`, `alpha`, and `shape` aesthetics to your graph.
Experiment.

<details class="code-fold">
<summary>Code</summary>

``` r
# Creates scatter plot with in-built mpg dataset, and modifies the looks of the plot.
ggplot(data = mpg) +
  geom_point(mapping = aes(x = displ,
                           y = hwy,
                           color = class)) + 
  labs(x = "Engine Displacement (L)",
       y = "Highway Mileage (mpg)",
       color = "Vehicle Class") +
  theme_light()
```

</details>

![](Week-4-Visualize-Exercises_files/figure-commonmark/Fifth%20Visualization%20-%20Scatter%20Plot%20with%20Colors%20and%20Titles-1.png)

## Help Me

What do `facet_grid()` and `facet_wrap()` do? (run the code, interpret,
convince your group)

<details class="code-fold">
<summary>Code</summary>

``` r
# Creates several scatter plots with in-built mpg dataset, and seperates data based on specified variables.
q <- ggplot(mpg) + geom_point(aes(x = displ, y = hwy))

q + facet_grid(. ~ cyl)
```

</details>

![](Week-4-Visualize-Exercises_files/figure-commonmark/Test%20Visualization%20-%20Scatter%20Plots%20Seperated%20by%20Other%20Variables-1.png)

<details class="code-fold">
<summary>Code</summary>

``` r
q + facet_grid(drv ~ .)
```

</details>

![](Week-4-Visualize-Exercises_files/figure-commonmark/Test%20Visualization%20-%20Scatter%20Plots%20Seperated%20by%20Other%20Variables-2.png)

<details class="code-fold">
<summary>Code</summary>

``` r
q + facet_grid(drv ~ cyl)
```

</details>

![](Week-4-Visualize-Exercises_files/figure-commonmark/Test%20Visualization%20-%20Scatter%20Plots%20Seperated%20by%20Other%20Variables-3.png)

<details class="code-fold">
<summary>Code</summary>

``` r
q + facet_wrap(~ class)
```

</details>

![](Week-4-Visualize-Exercises_files/figure-commonmark/Test%20Visualization%20-%20Scatter%20Plots%20Seperated%20by%20Other%20Variables-4.png)

## Your Turn 6

Make a bar chart `class` colored by `class`. Use the help page for
`geom_bar` to choose a “color” aesthetic for class.

<details class="code-fold">
<summary>Code</summary>

``` r
# Creates a bar plot with several other visualization options.
ggplot(data = mpg) +
  geom_bar(aes(x = class, fill = class)) +
  guides(fill="none") + 
  labs(x = "Vehicle Class",
       y = "Frequency",
       color = "Vehicle Class") +
  theme_light()
```

</details>

![](Week-4-Visualize-Exercises_files/figure-commonmark/Sixth%20Visualization%20-%20Bar%20Plot%20with%20Additional%20Modifications-1.png)

## Quiz

What will this code do?

<details class="code-fold">
<summary>Code</summary>

``` r
# Creates and saves a plot to a .jpg image file.
ggplot(mpg, aes(x = displ, y = hwy)) + 
  geom_point(aes(color=class)) +
  geom_smooth() 
```

</details>

    `geom_smooth()` using method = 'loess' and formula = 'y ~ x'

![](Week-4-Visualize-Exercises_files/figure-commonmark/Quiz%20-%20Scatter%20Plot%20and%20Saving%20Plots-1.png)

<details class="code-fold">
<summary>Code</summary>

``` r
  ggsave("example.jpg")
```

</details>

    Saving 7 x 5 in image
    `geom_smooth()` using method = 'loess' and formula = 'y ~ x'

------------------------------------------------------------------------

# Take aways

You can use this code template to make thousands of graphs with
**ggplot2**.

<details class="code-fold">
<summary>Code</summary>

``` r
ggplot(data = <DATA>) +
  <GEOM_FUNCTION>(mapping = aes(<MAPPINGS>))
```

</details>
