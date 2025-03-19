---
layout: default
title: Animated and interative plots
nav_order: 7
parent: Workshop content
has_toc: false
editor_options: 
  markdown: 
    wrap: 72
---

# Animated and Interative plots

***This code can take time to run, so we will go through it here instead
of in RMarkdown.*** <br/><br/>

We are going to make a plot with a slider. This allows users to interact
with the plot, which is very fun. If you want to learn more about this,
you can check out our <a href="https://ubc-library-rc.github.io/intro_shiny_app/" target="_blank"> workshop on how to make RShiny</a>

``` r
#Nice to have packages
library(gganimate) # package for producing gifs, extension of ggplot2
library(plotly)
library(gganimate)
library(gifski)
library(htmlwidgets)

## plot code
plot1 <- ggplot(aes(
  x = log(gdpPercap),
  y = lifeExp,
  frame = year
), #adding frame to aes
data = countries) +
  geom_point(aes(color = continent)) +
  labs(title = "Life expectancy vs GDP per capita through time",
       x = "Log 10 of GDP per capita",
       y = "Life expectancy") +
  geom_smooth(aes(color = continent), method = "lm", se = FALSE) +
  theme_bw()

ggplotly(plot1)

#save the object as an html file, using htmlwidget package
plotly1 <- ggplotly(plot1)
saveWidget(as_widget(plotly1), "plotly1.html")
```


[Click to view plot](plotly1.html) <br/><br/>
