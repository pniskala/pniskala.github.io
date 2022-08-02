---
title: "Can you make slides with Inkscape? Yes you can!"
date: 2022-08-02T11:15:45+03:00
draft: false
---

*This is a blog post I made on my old blog back in 2016. To be completely honest, I am not using Inkscape to make presentations anymore, mostly because I did not like using the app on a Mac in the first place. Nevertheless, maybe somebody still finds this interesting!*

Besides death and taxes, there is another thing that is pretty sure in life: you will have to present stuff. This is especially true in the academic world. Since the beginning of my PhD project, I was struggling to find a good tool for preparing the presentations. There were some boundary conditions: I would prefer to prepare them on my Linux computer, have the output in PDF, and make it look nice. I tried Open Office (or Libre Office), Latex and Prezi amongst other things, but about a year ago I found my true match, and that is Inkscape.

![image](/images/slide_example2.png)

I know this sounds crazy, but Inkscape really gives me the control, flexibility and the fidelity I felt I was missing with the other tools. Of course, Inkscape is not the obvious choice for the job. It is an open source graphics editor, and as such not really designed for crafting presentations. However, since I had already been using Inkscape to create visuals for my Latex-based presentations, I figured that maybe I could get rid of the Latex part altogether.

People have produced pretty cool plugins and scripts for Inkscape for quite some time. One of them is JessyInk, which really tries to turn the software into a tool for making presentations. The idea is very nice: using JessyInk, you can produce very clean graphics, include some animations, and present the whole thing via an Internet browser of all things.

If I would be sure I would use my own laptop or another fixed platform for my presentations all the time, I could definitely work with JessyInk. Nevertheless, based on some experimentation on different operating systems and browsers, I could not fully rely on the presentations to be platform independent, and that was one of my core requirements.

Instead of using JessyInk, I ended up adopting some of its principles and moulding a workflow of my own around Inkscape. That workflow is pretty simple, actually. I use the layers in inkscape as slides and lay these layers on top of a basic template layer. For any exceptional slides (e.g. title slide), when I want to override the basic template, I can just overlay for example a white background on top of the template in the specific slide and layer. It does sound a lot of extra work, but once you have a good template to work with and get a comfortable workflow, it is very pleasing and decently fast. And most importantly, the end result can look pretty nice.

The most cumbersome part of the process has to do with converting nicely designed layers into an actual PDF file. Here I improvised a bit and wrote a Python script to do the heavy lifting. Basically I save the presentation as an SVG file, and the script extracts each slide from the file to a single PDF file, which are then combined into a multipage PDF to create the final presentation. The script also applies the correct slide numbers on the slides.

The workflow is not yet perfect. I have some ideas for practical improvements (stop using shadows and gradients everywhere) and crazy stupid extensions (loading bar instead of slide numbers?) for the future, but I really like the end results I get. I already got one of my officemates to use the same workflow, so maybe I am not crazy after all.

If you are interested in having a look or even trying it out, go ahead: the script and the template are available in [GitHub](https://github.com/pniskala/pyscape-presentation).

![image](/images/slide_example1.png)

