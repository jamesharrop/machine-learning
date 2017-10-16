Exploring the iris dataset using R
================

In a recent blog post I used Python to explore the iris dataset. This is an attempt to produce the same output, but using R.

Loading the dataset and an initial look at the data
---------------------------------------------------

``` r
# We have data on 150 iris flowers and 4 different features
head(iris)
```

    ##   Sepal.Length Sepal.Width Petal.Length Petal.Width Species
    ## 1          5.1         3.5          1.4         0.2  setosa
    ## 2          4.9         3.0          1.4         0.2  setosa
    ## 3          4.7         3.2          1.3         0.2  setosa
    ## 4          4.6         3.1          1.5         0.2  setosa
    ## 5          5.0         3.6          1.4         0.2  setosa
    ## 6          5.4         3.9          1.7         0.4  setosa

``` r
dim(iris)
```

    ## [1] 150   5

Create a scatter plot
---------------------

Let’s look at a scatter plot of the first 2 features (sepal length and sepal width).

These are some available colour palettes:

``` r
library(RColorBrewer)
display.brewer.all()
```

![](R_exploring_iris_files/figure-markdown_github-ascii_identifiers/unnamed-chunk-2-1.png)

Choose some colours and make a plot:

``` r
cols=brewer.pal(n=9,name="Set1")
cols_palette =c(cols[1], cols[5], cols[9])
cols_iris <- cols_palette[iris$Species]
plot(iris$Sepal.Length, iris$Sepal.Width, col=cols_iris, pch=19)
```

![](R_exploring_iris_files/figure-markdown_github-ascii_identifiers/unnamed-chunk-3-1.png)

Plotting a scatter matrix:

``` r
pairs(iris[,1:4], col=cols_iris)
```

![](R_exploring_iris_files/figure-markdown_github-ascii_identifiers/unnamed-chunk-4-1.png)

A 3D plot of the first 3 features:

``` r
library(scatterplot3d)
scatterplot3d(iris$Sepal.Length, iris$Sepal.Width, iris$Petal.Length, color = cols_iris, pch = 19)
```

![](R_exploring_iris_files/figure-markdown_github-ascii_identifiers/unnamed-chunk-5-1.png)
