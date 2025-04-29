---
layout: project
parent: Reports
title: Learning-Based Segmentation & Grasping on FETCH with PointNet++ & AnyGrasp
description: Grasping opaque and transparent objects in real-world settings is hindered by noisy and incomplete point clouds. We present a pipeline on FETCH that uses Open3D for filtering, PointNet++ for learned segmentation, and AnyGrasp with MoveIt for accurate grasp prediction and execution.
authors:
  - name: Marzuk Kalluparamban
    social: "http://linkedin.com/in/marzukkp/"
    affiliation: University of Michigan
  - name: Hemanth Murali
    social: "https://hemanthmurali.me"
    affiliation: University of Michigan
  - name: Maithreyan Ganesh
    social: "https://www.linkedin.com/in/maithreyan-ganesh-5b248a207/"
    affiliation: University of Michigan
  - name: Jyotishka Dutta Gupta
    social: "https://www.linkedin.com/in/jyotishka-duttagupta/"
    affiliation: University of Michigan
---

<!-- Custom Styles -->
<style>
.table-small {
  width: 60%;
  margin: 0 auto;
  font-size: 0.85em;
  border-collapse: collapse;
}
.table-small th, .table-small td {
  border: 1px solid #ddd;
  padding: 6px 10px;
  text-align: center;
}
.table-small th {
  background-color: #f2f2f2;
}
.image-row {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 10px;
  margin-top: 15px;
}
.image-row img {
  width: 45%;
  height: auto;
}
.video-wrap {
  display: flex;
  justify-content: center;
  margin-top: 20px;
}
.video-container iframe {
  width: 80%;
  height: 400px;
}
</style>

<!-- Header Image -->
<div class="center-image">
<img alt="Teaser Figure" src="{{ site.baseurl }}/assets/projects/reports/FETCH-GRASP/DeepRob_gif.gif" />
</div>

<!-- Project Links -->
<div class="project-links" markdown="1">
[![]({{ site.baseurl }}/assets/logos/acrobat.svg){: .text-logo } Report](https://drive.google.com/file/d/1YXSGec71kHhcaW8yMMYBpGOa5UtkB80o/view?ts=68103a1a){: .btn .btn-grey .mr-6 target="_blank" rel="noopener noreferrer"}
[![]({{ site.baseurl }}/assets/logos/github-mark.svg){: .text-logo } Code](https://github.com/marzuk-umich/fetch_grasp){: .btn .btn-grey target="_blank" rel="noopener noreferrer" }
</div>

## Abstract

We demonstrate a real-world grasping pipeline that uses RGB-D data from a Kinect sensor installed on the FETCH robot to grasp opaque and partially transparent objects. We use a preprocessing pipeline that combines planar surface extraction using RANSAC, clustering with DBSCAN, and Open3D-based NaN removal to address noise, missing depth, and environmental clutter. Target isolation and object segmentation are performed using a PointNet++ model trained on augmented YCB point clouds. AnyGrasp is used to produce grasp candidates, which are then assessed using MoveIt’s inverse kinematics and collision checking framework. We compare the system’s performance on rigid and transparent objects in both isolated and cluttered scenarios. Grasp success rate and collision rate are used as key metrics, with additional testing on colorless and colored transparent objects.

## Introduction

Robotic grasping in unstructured environments remains a significant challenge due to perception uncertainty, object diversity, and planning constraints. In this project, we develop a real-world grasping pipeline for the FETCH mobile manipulator using RGB-D data from a Kinect sensor. The system integrates motion planning with MoveIt, grasp candidate generation with AnyGrasp, object segmentation with PointNet++, and point cloud preprocessing through Open3D filtering, RANSAC, and DBSCAN. The focus is on the implementation, deployment, and validation of the system on real hardware. Performance is evaluated on both rigid and transparent objects in isolated and cluttered settings, highlighting the strengths and limitations of the approach in practical robotic manipulation tasks.


## Methods

### Robust Grasp Perception: AnyGrasp

AnyGrasp provides dense and temporally consistent 7-DoF grasp pose predictions from partial point clouds. The system consists of a Geometry Processing Module, which samples and predicts stable grasp candidates using point-wise features, and a Temporal Association Module, which tracks grasps across frames for dynamic scenes using feature-based matching. Trained on real-world GraspNet-1Billion data with randomized point dropout, AnyGrasp achieves a 93.3% success rate in bin-picking tasks involving unseen objects.

<div class="image-row">
  <img src="{{ site.baseurl }}/assets/projects/reports/FETCH-GRASP/Anygrasp.png" alt="AnyGrasp Pipeline">
</div>

### Transparent Object Depth Completion: TransCG

To address the challenge of incomplete depth perception for transparent objects, TransCG introduces a real-world dataset and an efficient depth completion model, DFNet. DFNet refines noisy RGB-D inputs using dense blocks and a dual-loss strategy focusing on depth and surface normals. Trained on 57,715 images with augmentation, DFNet outperforms prior methods like ClearGrasp and demonstrates real-time performance, improving grasping reliability for transparent and translucent objects.

<div class="image-row">
  <img src="{{ site.baseurl }}/assets/projects/reports/FETCH-GRASP/transcg.png" alt="TransCG Pipeline">
</div>

## Results

### Effect of Object Rigidity

Grasping performance differs notably between rigid and deformable objects. Rigid objects tend to yield higher success rates and lower collision rates, likely due to their stable structural properties that are better aligned with traditional robotic grasping strategies. In contrast, deformable objects introduce complexities such as unpredictable shape changes and instability during grasping, often resulting in increased accidental contacts and reduced reliability. These challenges highlight the limitations of current grasping systems, which historically have been tuned for rigid environments. Advancements in perception, modeling, and adaptive control will be essential to more effectively handle the nuances of deformable object manipulation moving forward.

#### Table I
<table class="table-small">
  <thead>
    <tr>
      <th>Object Type</th>
      <th>Success Rate</th>
      <th>Collision Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Rigid</td>
      <td>70%</td>
      <td>15%</td>
    </tr>
    <tr>
      <td>Deformable</td>
      <td>67%</td>
      <td>27%</td>
    </tr>
  </tbody>
</table>

<div class="image-row">
  <img src="{{ site.baseurl }}/assets/projects/reports/FETCH-GRASP/rigid_grasp.png" alt="Rigid Grasp 1">
  <img src="{{ site.baseurl }}/assets/projects/reports/FETCH-GRASP/rigid_grasp_2.png" alt="Rigid Grasp 2">
</div>

### Effect of Environment Clutter

Grasping performance varies significantly between isolated and cluttered environments. In isolated settings, success rates are notably higher, reflecting the reduced complexity and minimal interference from surrounding objects. In contrast, cluttered environments introduce challenges such as the need to navigate around neighboring objects, resulting in lower grasp success rates and the occurrence of collisions. The close proximity of multiple objects, combined with irregular surfaces—especially when deformable objects are involved—complicates grasp planning and reduces overall stability. These observations reinforce the necessity for more robust grasping strategies capable of dynamically adapting to cluttered and unstructured scenes, an essential consideration for advancing practical robotic manipulation systems.

#### Table II
<table class="table-small">
  <thead>
    <tr>
      <th>Scene Type</th>
      <th>Success Rate</th>
      <th>Collision Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Isolated</td>
      <td>75%</td>
      <td>0%</td>
    </tr>
    <tr>
      <td>Cluttered</td>
      <td>70%</td>
      <td>Clutter collisions</td>
    </tr>
  </tbody>
</table>

<div class="image-row">
  <img src="{{ site.baseurl }}/assets/projects/reports/FETCH-GRASP/transcg1.png" alt="Transparent Grasp 1">
  <img src="{{ site.baseurl }}/assets/projects/reports/FETCH-GRASP/transcg2.png" alt="Transparent Grasp 2">
</div>

### Effect of Object Transparency

Grasping transparent objects presents substantial challenges compared to opaque ones. Performance metrics reveal that success rates are considerably lower for transparent objects, primarily due to limitations in depth sensing and perception. Despite the application of depth completion techniques, incomplete or noisy depth data frequently undermines the stability of initial grasp attempts. Interestingly, while grasp failures were common, collision rates remained low, suggesting that the primary difficulty lies not in avoiding obstacles but in establishing reliable grasp points. These results emphasize a critical gap in current robotic perception systems and highlight the pressing need for more advanced methods tailored specifically to handling transparent materials in complex environments.


#### Table III
<table class="table-small">
  <thead>
    <tr>
      <th>Object Material</th>
      <th>Success Rate</th>
      <th>Collision Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Opaque</td>
      <td>70%</td>
      <td>15%</td>
    </tr>
    <tr>
      <td>Transparent</td>
      <td>30%</td>
      <td>0%</td>
    </tr>
  </tbody>
</table>

<div class="image-row">
  <img src="{{ site.baseurl }}/assets/projects/reports/FETCH-GRASP/deform1.png" alt="Deformable Grasp 1">
  <img src="{{ site.baseurl }}/assets/projects/reports/FETCH-GRASP/deform2.png" alt="Deformable Grasp 2">
</div>



## Project Video

We demonstrate a real-world robotic grasping pipeline using FETCH, combining RGB-D sensing, PointNet++-based segmentation, and AnyGrasp for 6-DoF grasp prediction. Our system handles both opaque and partially transparent objects in isolated and cluttered environments. Below, we showcase the project demo of our project.

<div class="video-wrap">
  <div class="video-container">
	<iframe src="https://www.youtube.com/embed/pX7bedyRPV8?si=k0PWgBK2a9ul2UNH" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
  </div>
</div>


## Conclusion

In this project, we developed a modular robotic grasping system on the FETCH platform, capable of handling rigid, deformable, and transparent objects using RGB-D sensing, depth completion, PointNet++ segmentation, and AnyGrasp. While the system achieved strong performance on rigid and isolated objects, challenges remain in cluttered and transparent scenarios due to incomplete depth data and planning limitations. Future work will focus on enhancing transparent object perception, incorporating closed-loop feedback, and improving grasp planning to better approach human-level manipulation performance.



## Citation

If you found our work helpful, consider citing us with the following BibTeX reference:

```
@article{marzuk-umich2025sdeeprob,
  title = {Learning-Based Segmentation & Grasping on FETCH with PointNet++ & AnyGrasp},
  author = {Marzuk Kalluparamban, Hemanth Murali, Maithreyan Ganesh, and Jyotishka Dutta Gupta},
  affiliation = {University of Michigan},
  year = {2025}
}
```
Be sure to update this reference to include your team's author information for correct attribution!


## Contact

If you have any questions, feel free to contact [Marzuk Kalluparamban and Hemanth Murali](mailto:marzukkp@umich.edu?cc=hems@umich.edu).

