---
layout: project
parent: Reports
title: Improving the Robustness of Object Detection Under Hazardous Conditions
description: This is a final project report for DeepRob at the University of Michigan.
authors:
  - name: Rui Li
    affiliation: University of Michigan
  - name: Yuqing Luo
    affiliation: University of Michigan
  - name: Inbum Park
    affiliation: University of Michigan
  - name: Ziyang Xuan
    affiliation: University of Michigan
---


<!-- This is the project main image -->
<div class="center-image">
<img alt="Teaser Figure" src="{{ site.baseurl }}/assets/projects/reports/example/head_img.png"/>
</div>


<!-- This is the project pdf file and github code link -->
<div class="project-links" markdown="1">
[![]({{ site.baseurl }}/assets/logos/acrobat.svg){: .text-logo } Report](/w25/assets/projects/reports/example/DeepRob_Project_Group13.pdf){: .btn .btn-grey .mr-6 }
[![]({{ site.baseurl }}/assets/logos/github-mark.svg){: .text-logo } Code](https://github.com/inbumpark/DeepRobGroup13/blob/main/README.md){: .btn .btn-grey target="_blank" rel="noopener noreferrer" }
</div>


## Abstract

In this project, we evaluated the baseline performance of DETR, a transformer-based object detector, under adverse weather conditions using the DAWN dataset. We improved detection robustness by fine-tuning both the CNN backbone and transformer decoder, allowing the model to better handle low-visibility scenarios like rain, snow, fog, and sandstorms. Data augmentation techniques were also applied to simulate hazardous conditions and enhance generalization. Our results show that fine-tuning on domain-specific datasets improves performance, though challenges remain when dealing with diverse and severe weather. Future work will focus on integrating de-weathering modules to further boost detection reliability.


## Results

We compare the baseline model with two versions: a finetuned model ("Finetuned") and a deweathered model ("De-weathered"). Among the eight weather types in the DAWN dataset, 'dusttornado' is excluded due to having only two duplicate samples. Results are reported for six weather types — rain storm, sand storm, haze, mist, foggy, and snow storm — with sample counts ranging from 7 to 28. Evaluation follows the baseline metrics, using six Average Precision (AP) and six Average Recall (AR) scores. AP and AR are further broken down by object size (small, medium, large) and by maximum detections allowed (1, 10, 100). The IoU=0.5:0.95 metric represents an average over multiple IoU thresholds. The details in the result comparison for each test case can be found in the report. We also used the finetuned model on a bad weather driving vedio as shown below.


## Project Video

<div class="video-wrap">
  <div class="video-container">
	<iframe src="https://www.youtube.com/embed/KIGFfkhRxfU?si=lu8vLp5rwYBSp6BF" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
  </div>
</div>



## Citation

If you found our work helpful, consider citing us with the following BibTeX reference:

```
@inproceedings{detr,
  title={End-to-End Object Detection with Transformers},
  author={Carion, Nicolas and Massa, Francisco and Synnaeve, Gabriel and Usunier, Nicolas and Kirillov, Alexander and Zagoruyko, Sergey},
  booktitle={Proceedings of the European Conference on Computer Vision (ECCV)},
  year={2020},
  url={https://arxiv.org/abs/2005.12872}
}
```
Be sure to update this reference to include your team's author information for correct attribution!


## Contact

If you have any questions, feel free to contact [Inbum Park](mailto:ibpark@umich.edu).
