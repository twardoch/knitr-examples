# Print a code chunk as is

Sometimes we do not want to evaluate a chunk, and we just want to include a chunk literally, e.g. when writing tutorials. Two examples have been given:

- [062-chunk-wrapper.Rmd](https://github.com/yihui/knitr-examples/blob/master/062-chunk-wrapper.Rmd) ([output](https://github.com/yihui/knitr-examples/blob/master/062-chunk-wrapper.md))
- [062-chunk-wrapper.Rnw](https://github.com/yihui/knitr-examples/blob/master/062-chunk-wrapper.Rnw) ([output](https://github.com/yihui/knitr-examples/blob/master/062-chunk-wrapper.tex))

The R code chunks in these examples are still identified by **knitr**. If we do not want to evaluate the code at all, there is another approach, which is to break the chunk syntax by adding an empty string as _inline R code_.

For Markdown, we can add an empty string after ```` ```{r} ````; **knitr** will ignore this code chunk but also replace inline R code with the empty string. Here is one example (it is indented by 4 spaces because we want to show it in a preformatted block in the HTML output):

    ```{r eval=TRUE}
    n = 10
    rnorm(x)
    ```

By comparison, this chunk will be identified by **knitr** as usual:


``` r
n = 10
rnorm(n)
```

```
##  [1] -0.56048 -0.23018  1.55871  0.07051  0.12929  1.71506  0.46092
##  [8] -1.26506 -0.68685 -0.44566
```

Another way (discovered by Hadley Wickham) is to add a [zero-width space](http://en.wikipedia.org/wiki/Zero-width_space) in the chunk header, e.g.

    `​``{r eval=TRUE}
    n = 10
    rnorm(n)
    ```

Note the zero-width space is normally invisible in the web browser, and may also be invisible in your text editor. Trust me, there is a zero-width space after the first backtick in the above code chunk even if you cannot see it (the Emperor does have clothes). The RStudio IDE can show it as a red dot.
