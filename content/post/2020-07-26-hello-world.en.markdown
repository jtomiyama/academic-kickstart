---
title: Hello World
author: Joshua Tomiyama
date: '2020-07-26'
slug: hello-world
categories: []
tags: []
subtitle: ''
summary: ''
authors: []
lastmod: '2020-07-26T01:30:24-05:00'
featured: no
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []
---

Hello World! This is my first post on this blog.

As per instructions from the [academic theme documentation](https://sourcethemes.com/academic/docs/), I need to use a .Rmarkdown file rather than an .Rmd file.

Below is an R chunk:


```r
2 + 2 == 5
```

```
## [1] FALSE
```

Below is a (fun?) plot using R:


```r
curve(exp(0.3*(x - 18))/(1 + exp(0.3*(x - 18))), 
      main = 'Maturity level over time',
      xlab = 'Age', 
      ylab = 'Maturity level', 
      from = 0.1, 
      to = 25,
      ylim = c(0, 1))

curve(0.8*(x > 23) + 
      (1 - 0.1*(x - 21))*(x <= 23)*(x >21) + 
      1*(x >= 10)*(x <= 21) + 
      0.1*(x - 5)*(x < 10)*(x > 5),
      col = 'red',
      lwd = 2,
      add = TRUE)

legend('bottomright', 
       legend = c('Reality', 'Perceived'),
       lty = 1,
       col = c('black', 'red'))
```

<img src="/post/2020-07-26-hello-world.en_files/figure-html/unnamed-chunk-2-1.png" width="672" />

Look forward to mathy content!
