---
layout: page
title: Information Pursuit
description: an information-theoretic framework for making interpretable predictions.
img: assets/img/vip-thumbnail.png
importance: 1
category: Machine Learning
related_publications: true
---

**Background.**
As deep networks are more readily deployed in taking day-to-day decisons, interpretability of these processes are becoming more and more important. In fact, the European Union now requires
by law the "right to an explanation" for decisions made on individuals by algorithms. Initial efforts in this direction majorly focussed on <a href=""> post-hoc interpretability</a> of deep networks. However, post-hoc methods come with little guarantee as to whether the explanations they produce are accurate reflections of how the model makes its predictions. Consequently, in this project we focus on developing a framework for making predictions that is interpretable-by-design.

**What is interpretable prediction?**
Unlike privacy, where notions like differentiable privacy have become central to the development of privacy-preserving AI algorithms, a major challenge in interpretable ML is the lack of a definition for interpretability. This work focuses on interpretability to the user of an AI algorithm, who may not be AI experts themselves. In this context, we argue that interpretability of an ML decision ultimately depends on the end-user and the task. For instance, in image classification problems like bird identification, a model’s predictions are considered interpretable if they can be explained through salient parts of the image whereas in medical imaging, a more detailed explanation in terms of causality and mechanism is desired. 

Furthermore, interpretable explanations are often compositional, constructed from a
set of elementary units, like words in text or parts of an image. We propose to capture this user-dependent, task-specific and compositional property of explanations via the concept of a query set.
Query sets are sets of functions, that are task-specific and interpretable to the user. For example,
if the task is bird species identification from images, a potential query set could consist of questions
about the presence/absence of different visual attributes of birds like beak shape, feather colour
and so on. Given such a query set, how do we make interpretable predictions? 

**Interpretable predictions by playing 20 questions.**
Given a query set, we propose to make predictions by playing the popular parlor game, 20 questions. In this game, the ML model sequentially asks queries about the given input (from the query set). Each query choice depends on the query-answers obtained in the sequence so far. Once, the model has obtained enough information from the query-answers a prediction is made. The query answers are either provided by an oracle (input features in data) or by classifiers trained on annotated query-answer datasets. This process is illustrated in the figure below.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/VIP-illustration.png.jpg" title="Interpretable predictions by IP" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Illustration of the framework for making interpretable
    predictions. The task is image classification.
    The user-specified query set Q consists of queries about the
    presence or absence of different semantic attributes of objects.
    Given an image, the model proceeds by selecting
    queries from Q until a prediction can be made with high
    confidence.
</div>
In the above figure, the given image is correctly classified as a “Bison” by sequentially
asking 10 queries about different characteristics of the image. This query-answer chain serves as
an explanation for why the model predicted this image as a Bison. Notice, shorter explanations
are easier to read and interpret than longer ones, thus along with making accurate predictions we
would like to promote shorter query-answer chains. 

**Information Pursuit: What query to ask next?**
Information Pursuit (proposed by Geman & Jedynak, 1996) is a greedy heuristic used in active testing problems where the goal is to select tests (queries in our context) to solve a task (prediction)
by carrying out the minimal number of tests on average. IP uses mutual information (MI) between the query answer and the prediction variable to decide which query to select next in the sequence. Unfortunately, computing MI is difficult in high dimensions. 

In {% cite chattopadhyay2022interpretable %} we propose a generative approach to the algorithm called Generative Information Pursuit, or G-IP. Specifically, we posit a graphical model wherein we assume the query answers to be conditionally independent of each other given the class label Y and some latent variable Z. This conditional independence allows for efficient computation of MI by sampling. The graphical model is learnt from data using Variational Autoencoders and the Unadjusted Langevin algorithm is utilized to carry out inference. Unlike previous approaches, this implementation of IP achieves competitive performance (for the first time) with deep networks (trained by taking all query answers as features) while being interpretable.


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

