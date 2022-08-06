---
title: "Working with Quarto and Hugo"
date: 2022-08-06T12:01:47+03:00
draft: false
tags:
- development
- communcation
- hugo
- web
categories:
- Development
- Communication
- Web
---

## Quick intro to Quarto

While exploring the offerings of [Fast.ai](https://www.fast.ai/), I got introduced to [Quarto](https://quarto.org/), a handy-looking open-source publishing system. 

In practice, Quarto allows publishing your work – were it code, data analysis, or just plain markdown text – in a variety of formats including PowerPoint, HTML, and so on.

As a practical example I decided to try Quarto out by creating a very quick data exploration notebook as the system has [a nice integration with Hugo](https://quarto.org/docs/output-formats/hugo.html). 

[This blog post about cars in Finland]() was actually created using a [Jupyter Notebook](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.suptitle.html). Here I will share some of my experiences.

## Quick takeaways from my test run with Hugo and Quarto

### 1. Quarto is easy to get started with

I quickly blazed through the Quarto tutorials to get an idea how you are expected work with the system. They do have good documentation so it was easy to get a good grasp of the basic functionalities. I was surprised that they even had the Hugo specific material available. It was super easy to get started and I was able to get a decent-looking output without too much fine-tuning.

### 2. The workflow is nice

Quarto's tooling enables a nice workflow where you can preview the output live as you are working on the document. With a bigger screen – i.e. not your laptop screen – you can easily have e.g. your Jupyter notebook on the left side and the preview of the output on the right side. This should be familiar to anyone working with web development and especially frontend stuff.

### 3. There is a wide variety of different formats

As mentioned earlier, Quarto supports a wide variety of different formats. Originally, for me the biggest draw was the HTML output as I can see that being most flexible and usable for sharing data science work, but I would like to try out generating Powerpoint and Reveal.js presentations as well. The nice thing about HTML output is the support for interactive visualizations.

### 4. I could not get Altair working with Hugo

I was ambitious and wanted to try out [Altair](https://altair-viz.github.io) while testing Quarto. Altair is a visualization library for Python, complementary to e.g. Plotly, Matplotlib, and Seaborn. It seems to provide nice interactive figures with a small amount of code. Unfortunately I did not manage to get Quarto, Hugo, and Altair co-operating as the website would not build with Altair visualizations included. Not a deal-breaker but it could also be just a user error.

### 5. The Hugo format does not support all of the fancy features

Quarto has some nice configuration options but not every knob applies to every format. I have to admit I did not really play around with the Hugo specific config arguments that much but I did notice that for example the code-folding parameter did not work for the Hugo format. For HTML outputs, you can use it to make your code snippets collapsible. Even though Quarto seems easy to get started with, it will definitely take some time to really master all the parameters and possibilities.

## Conclusions

I have to admit my test post about cars in Finland was not as exciting as I had hoped – although I am not sure what I was hoping get out of the data that quickly...

Nevertheless, I can see Quarto being very useful in documenting, demoing, and sharing code and data analysis in my data science work. I will definitely use it for more serious purposes soon.

For practical introduction in to Quarto, please check out [the official tutorials](https://quarto.org/docs/get-started/).

