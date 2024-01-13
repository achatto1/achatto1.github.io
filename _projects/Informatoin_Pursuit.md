---
layout: page
title: Information Pursuit
description: an information-theoretic framework for making interpretable predictions.
img: assets/img/vip-thumbnail.png
importance: 1
category: Machine Learning
related_publications: true
---

**Background**
As deep networks are more readily deployed in taking day-to-day decisons, interpretability of these processes are becoming more and more important. In fact, the European Union now requires
by law the "right to an explanation" for decisions made on individuals by algorithms. Initial efforts in this direction majorly focussed on <a href=""> post-hoc interpretability</a> of deep networks. However, post-hoc methods come with little guarantee as to whether the explanations they produce are accurate reflections of how the model makes its decisions. Consequently, in this project we focus on developing a framework for making decisions that is interpretable-by-design.

**What is interpretable explanation?**
Unlike privacy, where notions like differentiable privacy have become central to the development of privacy-preserving AI algorithms, a major challenge in interpretable ML is the lack of a definition for interpretability. This work focuses on interpretability to the user of an AI algorithm, who may not be AI experts themselves. In this context, we argue that interpretability of an ML decision ultimately depends on the end-user and the task. For instance, in image classification problems like bird identification, a model’s decisions are considered interpretable if they can be explained through salient parts of the image whereas in medical imaging, a more detailed explanation in terms of causality and mechanism is desired. 

Furthermore, interpretable explanations are often compositional, constructed from a
set of elementary units, like words in text or parts of an image. We propose to capture this user-dependent, task-specific and compositional property of explanations via the concept of a query set.
Query sets are sets of functions, that are task-specific and interpretable to the user. For example,
if the task is bird species identification from images, a potential query set could consist of questions
about the presence/absence of different visual attributes of birds like beak shape, feather colour
and so on. 




<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    This image can also have a caption. It's like magic.
</div>

You can also put regular text between your rows of images, even citations {% cite einstein1950meaning %}.
Say you wanted to write a bit about your project before you posted the rest of the images.
You describe how you toiled, sweated, *bled* for your project, and then... you reveal its glory in the next row of images.


<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    You can also have artistically styled 2/3 + 1/3 images, like these.
</div>


The code is simple.
Just wrap your images with `<div class="col-sm">` and place them inside `<div class="row">` (read more about the <a href="https://getbootstrap.com/docs/4.4/layout/grid/">Bootstrap Grid</a> system).
To make images responsive, add `img-fluid` class to each; for rounded corners and shadows use `rounded` and `z-depth-1` classes.
Here's the code for the last row of images above:

{% raw %}
```html
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
```
{% endraw %}
