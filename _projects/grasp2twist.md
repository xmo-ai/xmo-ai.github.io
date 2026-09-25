---
layout: page
title: "Grasp2Twist: Learning Bimanual Dexterous Jar Opening by Reinforcement Learning"
description: Bimanual dexterous jar opening with a single RL policy, transferred zero-shot to hardware
permalink: /projects/grasp2twist/
nav: false
img: assets/img/projects/grasp2twist/sim2real_setup.png
importance: 1
category: work
related_publications: false
---

**Mo Xu**, Yunfu Deng, Jianuo Wang, Josiah Hanna<sup>&dagger;</sup>, Bilge Mutlu<sup>&dagger;</sup>

University of Wisconsin-Madison &nbsp;&middot;&nbsp; <sup>&dagger;</sup>Equal senior authors

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/grasp2twist/sim2real_setup.png" title="Grasp2Twist real-world and simulated setup" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Real-world and simulated bimanual dexterous jar opening with two robot arms and dexterous hands.
</div>

## Abstract

Grasp2Twist is a bimanual dexterous manipulation system that learns to grasp and twist open jar lids with reinforcement learning.
Learning this task raises three challenges: learning a unified policy for a multi-stage task, sustaining lid twisting, and sim-to-real transfer.
We introduce a continuous enclosure measure to guide grasp formation and a binary enclosure indicator to guide the grasp-to-twist transition,
both derived from the geometric relationship between the object center and the convex hull formed by the palm and fingertips.
Because kinematic constraints limit how far the hand can rotate the lid with fixed contacts, sustained twisting requires finger contact reconfiguration;
a three-stage curriculum facilitates exploration of these contact changes and improves robustness for sim-to-real transfer.
The learned policy demonstrates finger gaiting, transfers zero-shot to the physical system, and achieves an **88% success rate** across six household containers.

## Method

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/projects/grasp2twist/geom_repre_simplified.png" title="Hand-object enclosure" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The palm and fingertips form a convex hull; its relation to the object center guides grasp formation and the grasp-to-twist transition.
</div>

A three-stage curriculum then drives finger-gait exploration and sim-to-real robustness.

## System

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/projects/grasp2twist/BimanualDexSys.png" title="Real-world system overview" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    Real-world system with vision, policy, and driver nodes on two Franka arms with TESOLLO dexterous hands.
</div>

## Real-World Results

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/projects/grasp2twist/real_sequence.png" title="Real-world execution sequence" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    From pre-grasp to lid removal: the holding hand stabilizes the jar body while the twisting hand rotates the lid, with fingers asynchronously twisting, releasing, repositioning, and re-establishing contact.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/projects/grasp2twist/real_world_instances.jpg" title="Real-world test instances" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    Test objects: an in-distribution 3D-printed jar (left) and six out-of-distribution household containers.
</div>

- On the six household containers, the policy succeeds in **53/60 trials (88%)**, compared with 18/60 (30%) for an open-loop replay baseline.
- On the 3D-printed jar, it achieves a mean cumulative lid rotation of about 7.1&pi; rad with 45 finger-gait events within 30 seconds.
