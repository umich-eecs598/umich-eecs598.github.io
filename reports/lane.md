---
layout: project
parent: Reports
title: "Dynamic Weather-Aware Lane Detection"
description: "Final project report for DeepRob at the University of Michigan."

authors:
  - name: "Justin Boverhof"
    affiliation: "University of Michigan"
    year: "Robotics"
  - name: "Joseph Fedoronko"
    affiliation: "University of Michigan"
    year: "Robotics"
  - name: "Anay Moitra"
    affiliation: "University of Michigan"
    year: "Computer Science"
  - name: "Andrew Rodriguez"
    affiliation: "University of Michigan"
    year: "Robotics"
---


<!-- This shows how to add an image (or gif) in markdown -->
<div class="center-image">
<img alt="Teaser Figure" src="{{ site.baseurl }}/assets/projects/reports/lane/FPN.png" />
</div>


<!-- <div class="project-links" markdown="1">
[![]({{ site.baseurl }}/assets/logos/acrobat.svg){: .text-logo } Report](#){: .btn .btn-grey .mr-6 }
[![]({{ site.baseurl }}/assets/logos/github-mark.svg){: .text-logo } Code](https://github.com/opipari/DeepRobWeb/blob/w24/reports/example.md){: .btn .btn-grey target="_blank" rel="noopener noreferrer" }
</div> -->


## Abstract

Lane detection is a critical task for autonomous driving, enabling safe navigation by identifying road boundaries and lane structures. In this project, we enhance the Ultra Fast Lane Detection (UFLD) framework to improve its robustness under challenging conditions, such as adverse weather and low visibility. Our contributions include the integration of a Feature Pyramid Network (FPN) for multi-scale feature extraction, a dynamic weather prompting mechanism to adapt the model based on current environmental conditions, and an unsupervised weather discovery system to eliminate the need for manual weather labeling. Together, these improvements enable real-time, weather-adaptive lane detection, demonstrating strong potential for practical deployment in autonomous systems operating in diverse environments.

## Our Extensions
In order to address the concernes we had about lane detection in adverse weather conditions, we implemented an FPN layer after the backbone with the goal of improving on the original resnet-18 feature extraction. Additionally, we experiemented with dynamic prompting as another solution to lane detection in bad conditions. We designed a weather condition module that encodes the current weather as a learnable embedding. Each weather type (clear, rain, snow, fog) is represented initially as a one-hot vector, which is projected into a dense embedding space through a small multi-layer perceptron (MLP). This weather embedding is then concatenated with the feature map output from the backbone network. We introduced a fusion MLP to process combined features and extended the parsingNet lane detection model to accept a weather_condition input, ensuring weather-aware features throughout. The data loader was updated to supply weather prompts during training and inference, enabling dynamic prompting that improves detection across conditions without needing separate models.

## Results

To validate the results of our methodology, we decided to train both two models, one without the addition of a simple weather-aware classifier and one with it. Both were trained for 2 epochs. We then utilized the built in evaluation command that came with the UFLD paper to see the precision, recall, and the F1 scores. For our tests, we were able to evaluate the model without any additions in all the different environment but did a basic score for the model with additions.

### Table 1. Precision, Recall, and F1 Score for the Colab Dynamic Prompting Demonstration.

| Experiment                | Precision | Recall | F1    |
|----------------------------|-----------|--------|-------|
| Colab Dynamic Prompting    | 0.9876    | 0.9853 | 0.9890 |

To validate our dynamic prompting and clustering pipeline, we ran a lightweight experiment on 1000 CULane images. Features were clustered into four groups, and a simple weather-aware classifier trained on these clusters achieved high performance, confirming our method's effectiveness at modeling weather variations with limited supervision.

## Citation

```
@article{DynamicWeatherLaneDetection2025deeprob,
  title = {FPN Lane Detection},
  author = {Boverhof, Justin and Fedoronko, Joseph and Moitra, Anay and Rodriguez, Andrew},
  year = {2025}
}
```
