---
layout: default
title: Animated and interative plots
nav_order: 7
parent: Workshop content
has_toc: false
---

# Animated and Interative plots
***This code can take time to run, so we will go through it here instead of in RMarkdown.***
<br/><br/>

We can take our plot of GDP per capita vs life expectancy by year: 

![](/regplot.png)
<br/><br/>

and instead ***animate it***, to have one plot: 

Input
{: .label .label-green }
```sh
countries$year<-as.numeric(countries$year) #need our data to be numeric instead of categorical for this

gif_countries <- 
  ggplot(aes(x=log(gdpPercap), y=lifeExp), 
         data = countries)+
      geom_point(aes(col = continent), alpha = 0.75)+
      scale_colour_viridis(discrete = TRUE)+
      transition_time(year)+ #creating gif through time
      shadow_wake(wake_length = 0.5)+ #adding tails
      labs(title="Life expectancy vs GDP per  capita in {frame_time}",
           x="Log 10 of GDP per capita", 
           y="Life expectancy")+ 
  theme_bw()

gif_countries

#can save with:
anim_save("countries.gif", animation = gif_countries, path = NULL)
```

Output
{: .label .label-yellow }
![Animated plot](https://media.giphy.com/media/TaizJ94JHqZb13iwuE/giphy.gif)
<br/><br/>

we could also ***make this plot interactive***. We will start with restricting our data to 2007. 

Input
{: .label .label-green }
```sh
countries07 <- countries[countries$year==2007,] #filtering data to 2007

plot07 <- ggplot(aes(x=log(gdpPercap), y=lifeExp), data = countries07)+
      geom_point(aes( color=continent))+
      labs(title="Life expectancy vs GDP per capita, 2007",
           x="Log 10 of GDP per capita", 
           y="Life expectancy")+
      geom_smooth(aes(color=continent), method="lm", se=FALSE) + 
  scale_colour_viridis(discrete = TRUE) +
  theme_bw()

ggplotly(plot07) #making interactive

#can save with: 
plotly07<-ggplotly(plot07)
saveWidget(as_widget(plotly07), "plotly07.html")
```

Output
{: .label .label-yellow }

[Click to view plot](/plotly07.html)
<br/><br/>

We could add year as a frame so that we can see changes over time:

Input
{: .label .label-green }
```sh
plot1 <- ggplot(aes(x=log(gdpPercap), y=lifeExp, 
                    frame=year), #adding frame to aes
                    data = countries)+
       geom_point(aes(color=continent))+
      labs(title="Life expectancy vs GDP per capita, 2007",
           x="Log 10 of GDP per capita", 
           y="Life expectancy")+
      geom_smooth(aes(color=continent), method="lm", se=FALSE) + 
  scale_colour_viridis(discrete = TRUE) +
  theme_bw()

ggplotly(plot1)

#save the object as an html file, using htmlwidget package
plotly1<-ggplotly(plot1)
saveWidget(as_widget(plotly1), "plotly1.html")
```
Output
{: .label .label-yellow }

[Click to view plot](/plotly1.html)
<br/><br/>