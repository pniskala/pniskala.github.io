---
title: "MMM with LLM: Meta officially announces the relase of RobynPy"
date: 2025-01-10T14:15:47+03:00
draft: false
tags:
- marketing
- data science
- open source
categories:
- Marketing
- Data science
---

![image](/images/robyn_github.png)

Meta has [officially released](https://developers.facebook.com/blog/post/2024/12/19/announcing-the-python-version-of-project-robyn) the Python version of its open source Marketing Mix Modelling (MMM) library Robyn – finally, may I say!

Robyn was originally developed in R and released in 2021. I think it was also around 2021 or 2022 when I tried it out the first time, and the project has definitely progressed since then.

Marketing Mix Modelling is a statistical method for estimating the incremental impact of marketing. It has gained some traction in recent years mainly due to privacy trends that have raised questions about the feasibility of digital attribution. It also helps in estimating 

Under the hood, Robyn stands out from many other MMM packages by using Nevergrad for multi-objective optimization of model parameters whereas e.g. Google's Meridian and PyMC Marketing go for the Bayesian approach.

I am of course biased towards Python and this is still a beta release but the Python version will most certainly make the project more accessible and increase its adoption.

It will be interesting to see how they develop and maintain the R and Python versions going forward and what kind of a feature parity they will achieve between the versions. In addition to the native Python version, there seems to be an API wrapper that should allow using the latest R version via Python as a fallback.

I have not played around with the Python release too much but at least getting started and running the example notebooks was easy enough.

According to Meta, the conversion from R to Python has heavily utilized Large Language Models – creating MMMs with LLMs. The library itself itself does not of course contain any LLM elements.

I have not dug deep enough into the code to compare the R and Python code and to deduce how much human touch has been involved in the translation. However, I did receive a comment on Linkedin saying that Python version could barely be called a "library", given the effort put into the translation.

The repository for the project can be found [here](https://github.com/facebookexperimental/Robyn).
