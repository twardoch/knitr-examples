% Writing beautiful and reproducible slides quickly
% Yihui Xie
% 2012/04/30



# Why

- after you finished typing `\documentclass{beamer}` and `\title{}`, I have finished my first slide with markdown
- far fewer commands to remember, e.g. to write bullet points, just begin with a dash "`-`" instead of `\begin{itemize}` and `\item`; how things can be simpler?
- I know you want math to show you are a statistician, e.g. $f(k)={n \choose k}p^{k}(1-p)^{n-k}$
- you do not need to maintain output -- only maintain a source file
- HTML5/CSS3 is much more fun than LaTeX

# A bit R code


``` r
head(cars)
```

```
##   speed dist
## 1     4    2
## 2     4   10
## 3     7    4
## 4     7   22
## 5     8   16
## 6     9   10
```

``` r
cor(cars)
```

```
##        speed   dist
## speed 1.0000 0.8069
## dist  0.8069 1.0000
```

# Graphics too


``` r
library(ggplot2)
qplot(speed, dist, data = cars) + geom_smooth()
```

![A scatterplot of `cars`](https://db.yihui.org/knitr-examples/figure/009-slides-graphics-1.png)

# How

- source editor: [RStudio](http://www.rstudio.org/) (perfect integration with [**knitr**](http://yihui.org/knitr/); one-click compilation); currently you have to use the version >= 0.96.109
- HTML5 slides converter: [pandoc](http://johnmacfarlane.net/pandoc/); this document was generated by: `pandoc -s -S -i -t dzslides --mathjax knitr-slides.md -o knitr-slides.html`
- the file [`knitr-slides.md`](https://github.com/yihui/knitr-examples/blob/master/009-slides.md) is the markdown output from its [source](https://github.com/yihui/knitr-examples/blob/master/009-slides.Rmd): `library(knitr); knit('knitr-slides.Rmd')`
- or simple click the button `Knit HTML` in RStudio

# For ninjas

- you should tweak the default style; why not try some [Google web fonts](http://www.google.com/webfonts)? (think how painful it is to wrestle with fonts in LaTeX)
- pandoc provides 3 types of HTML5 slides (dzslides is one of them)
- you can tweak the default template to get better appearances
- if you have come up with a better dzslides template, please let me know or contribute to pandoc directly (e.g. `pre` blocks should have `max-width` and `max-height`)

# For beamer lovers

- pandoc supports conversion to beamer as well. period.

# For Powerpoint lovers

- ...

# Reproducible research

It is good to include the session info, e.g. this document is produced with **knitr**. Here is my session info:


``` r
print(sessionInfo(), locale = FALSE)
```

```
## R version 4.4.0 (2024-04-24)
## Platform: x86_64-pc-linux-gnu
## Running under: Ubuntu 22.04.4 LTS
## 
## Matrix products: default
## BLAS:   /usr/lib/x86_64-linux-gnu/openblas-pthread/libblas.so.3 
## LAPACK: /usr/lib/x86_64-linux-gnu/openblas-pthread/libopenblasp-r0.3.20.so;  LAPACK version 3.10.0
## 
## attached base packages:
## [1] stats     graphics  grDevices utils     datasets  methods   base     
## 
## other attached packages:
## [1] ggplot2_3.5.1 knitr_1.46.4 
## 
## loaded via a namespace (and not attached):
##  [1] vctrs_0.6.5      nlme_3.1-164     cli_3.6.2        rlang_1.1.3     
##  [5] xfun_0.44        highr_0.10.2     labeling_0.4.3   glue_1.7.0      
##  [9] colorspace_2.1-0 formatR_1.14     scales_1.3.0     fansi_1.0.6     
## [13] grid_4.4.0       munsell_0.5.1    evaluate_0.23    tibble_3.2.1    
## [17] lifecycle_1.0.4  compiler_4.4.0   codetools_0.2-20 pkgconfig_2.0.3 
## [21] mgcv_1.9-1       farver_2.1.2     lattice_0.22-6   digest_0.6.35   
## [25] R6_2.5.1         utf8_1.2.4       pillar_1.9.0     splines_4.4.0   
## [29] magrittr_2.0.3   Matrix_1.7-0     tools_4.4.0      withr_3.0.0     
## [33] gtable_0.3.5
```

# Misc issues

- the plots are too wide? use the chunk option `out.width` which will be used in `<img width=... />`, e.g. `out.width=400px`

# Life is short

- so keep your audience awake!

    ![](http://i.imgur.com/qBO9K.jpg)
