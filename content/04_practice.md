---
layout: default
title: Practice problems
nav_order: 9
parent: Workshop content
has_toc: false
permalink: /content/practice.html
---

# GGPLOT2 Practice
All of these problems use the iris dataset. For the problems in the same section, you are building off the same plot code. Use online tools as needed (Google, ChatGPT) to find the answers as needed.

## Section 1 - box plot

**P1.** Make a boxplot of petal length by iris species.

<details open markdown="1"><summary>Answer</summary>

``` r
ggplot(iris, aes(x=Species, y=Petal.Length))+
  geom_boxplot()
```

</details>

**P2.** Rename the x and y axes.

<details open markdown="1"><summary>Answer</summary>

``` r
ggplot(iris, aes(x=Species, y=Petal.Length))+
  geom_boxplot()+
  labs(x="Iris Species", y="Petal Length")
```

</details>

**P3.** Color the box outline and fill by iris species.

<details open markdown="1"><summary>Answer</summary>

``` r
ggplot(iris, aes(x=Species, y=Petal.Length, fill=Species, color=Species))+
  geom_boxplot()+
  labs(x="Iris Species", y="Petal Length")
```

</details>

**P4.** Make the fill more transparent to be able to see the outline and median of the boxplots.

<details open markdown="1"><summary>Answer</summary>

``` r
ggplot(iris, aes(x=Species, y=Petal.Length, fill=Species, color=Species))+
  geom_boxplot(alpha=0.3)+
  labs(x="Iris Species", y="Petal Length")
```

*Note: smaller alpha is more transparent. 1 = fully opaque, 0 = fully transparent.*

</details>

**P5.** Change the fill and color to custom colors. You can use any colors you want. I like [this website](https://htmlcolorcodes.com/color-picker/) to find colors.

<details open markdown="1"><summary>Answer</summary>

``` r
ggplot(iris, aes(x=Species, y=Petal.Length, fill=Species, color=Species))+
  geom_boxplot(alpha=0.3)+
  labs(x="Iris Species", y="Petal Length")+
  scale_color_manual(values=c("#7b01a0","#a07b01","#01a07b"))+
  scale_fill_manual(values=c("#7b01a0","#a07b01","#01a07b"))
```

</details>

**P6.** Change the color and size of the axes labels.

<details open markdown="1"><summary>Answer</summary>

``` r
ggplot(iris, aes(x=Species, y=Petal.Length, fill=Species, color=Species))+
  geom_boxplot(alpha=0.3)+
  labs(x="Iris Species", y="Petal Length")+
  scale_color_manual(values=c("#7b01a0","#a07b01","#01a07b"))+
  scale_fill_manual(values=c("#7b01a0","#a07b01","#01a07b"))+
  theme(axis.text = element_text(colour = "black", size = 10))
```

</details>

## Section 2 - Dot plots/scatter plot

**P7.** Make a dot plot of petal length and petal width. Add linear regression lines to fit the points. Color the lines and the points by species.

<details open markdown="1"><summary>Answer</summary>

``` r
ggplot(iris, aes(x=Petal.Width, y=Petal.Length, color=Species))+
  geom_point()+
  geom_smooth(method="lm")
```

</details>

## Section 3 - Histograms

**P8.** Make a histogram of petal width and color the bars by species.

<details open markdown="1"><summary>Answer</summary>

``` r
ggplot(iris, aes(x=Petal.Width, fill=Species))+
  geom_histogram()
```

</details>
