---
layout: default
title: Practice problems
nav_order: 9
parent: Workshop content
has_toc: false
---

# GGPLOT2 Practice
All of these problems use the iris dataset. For the problems in the same section, you are building off the same plot code. Use online tools as needed (Google, ChatGPT) to find the answers as needed.

## Section 1 - box plot
P1: Make a boxplot of petal length by iris species. 

<details><summary><strong> Answer P1</strong></summary>
ggplot(iris, aes(x=Species, y=Petal.Length))+
  geom_boxplot()
</details>

P2: Rename the x and y axes
<details><summary><strong> Answer P2</strong></summary>
<p>ggplot(iris, aes(x=Species, y=Petal.Length))+</p>
<p>  geom_boxplot()+</p>
 <p> <strong>labs(x="Iris Species", y="Petal Length")</strong></p>
</details>

P3: Color the box outline and fill by iris species. 
<details><summary><strong> Answer P3</strong></summary>
<p>ggplot(iris, aes(x=Species, y=Petal.Length, <strong>fill=Species, color=Species</strong>))+</p>
 <p> geom_boxplot()+</p>
 <p> labs(x="Iris Species", y="Petal Length")</p>
</details>

P4: Make the fill more transparent to be able to see the outline and median of the boxplots.
<details><summary><strong> Answer P4</strong></summary>
<p>ggplot(iris, aes(x=Species, y=Petal.Length, fill=Species, color=Species))+</p>
 <p> geom_boxplot(<strong>alpha=0.3</strong>)+</p>
 <p> labs(x="Iris Species", y="Petal Length")</p>
  <p>Note, smaller alpha is more transparent.1 = full opaque, 0 = fully transparent. </p>
</details>

P5: Change the fill and color to custom colors. You can use any colors you want. I like <a href="https://htmlcolorcodes.com/color-picker/" target="_blank">this website</a> to find colors. 
<details><summary><strong> Answer P5</strong></summary>
<p>ggplot(iris, aes(x=Species, y=Petal.Length, fill=Species, color=Species))+</p>
 <p> geom_boxplot(alpha=0.3)+</p>
 <p> labs(x="Iris Species", y="Petal Length")</p>
 <p><strong>scale_color_manual(values=c("#7b01a0","#a07b01","#01a07b"))+</strong></p> 
   <p><strong>scale_fill_manual(values=c("#7b01a0","#a07b01","#01a07b"))</strong></p> 
</details>

P6: Change the color and size of the axes labels
<details><summary><strong> Answer P6</strong></summary>
<p>ggplot(iris, aes(x=Species, y=Petal.Length, fill=Species, color=Species))+</p>
 <p> geom_boxplot(alpha=0.3)+</p>
 <p> labs(x="Iris Species", y="Petal Length")</p>
 <p>scale_color_manual(values=c("#7b01a0","#a07b01","#01a07b"))+</p> 
   <p>scale_fill_manual(values=c("#7b01a0","#a07b01","#01a07b"))+</p> 
  <p><strong>theme(axis.text = element_text(colour = "black", size = 10))</strong></p>
</details>
