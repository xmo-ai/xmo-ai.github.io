---
layout: page
title: "Grasp2Twist: Learning Bimanual Dexterous Jar Opening by Reinforcement Learning"
description: Bimanual dexterous jar opening with a single RL policy, transferred zero-shot to hardware
permalink: /projects/grasp2twist/
nav: false
img: assets/img/projects/grasp2twist/teaser.jpg
importance: 1
category: work
related_publications: false
---

<style>
  :root {
    --g2t-teal: #1283a6;
    --g2t-purple: #4d2f87;
    --g2t-red: #e45b40;
    --g2t-green: #5ab946;
    --g2t-yellow: #f2c318;
    --g2t-teal-text: #1283a6;
    --g2t-purple-text: #4d2f87;
    --g2t-red-text: #e45b40;
  }
  html[data-theme="dark"] {
    --g2t-teal-text: #4db6d8;
    --g2t-purple-text: #b39ddb;
    --g2t-red-text: #f08c75;
  }
  .g2t-authors {
    font-size: 1.05rem;
    margin-bottom: 0.2rem;
  }
  .g2t-affil {
    color: var(--global-text-color-light);
    font-size: 0.9rem;
  }
  .g2t-links {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
    margin: 0.8rem 0 0;
  }
  .g2t-btn {
    border: 1px solid var(--global-theme-color);
    border-radius: 999px;
    padding: 0.2rem 0.9rem;
    font-size: 0.9rem;
  }
  .g2t-rule {
    display: flex;
    height: 4px;
    margin: 1rem 0 1.5rem;
  }
  .g2t-rule span {
    flex: 1;
  }
  .g2t-tldr {
    background: color-mix(in srgb, var(--g2t-teal) 9%, transparent);
    border-left: 4px solid var(--g2t-teal);
    border-radius: 6px;
    padding: 0.9rem 1.1rem;
    margin-bottom: 1.5rem;
  }
  .g2t-tldr p {
    margin: 0;
  }
  .g2t-tldr p.g2t-tldr-head {
    color: var(--g2t-teal-text);
    font-size: 1.15rem;
    font-weight: 600;
    margin-bottom: 0.3rem;
  }
  .g2t-narrow {
    max-width: 62%;
    margin: 0 auto;
  }
  .g2t-stages {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 0.9rem;
    margin: 0.8rem 0 1.5rem;
  }
  .g2t-stage {
    border: 1.5px solid var(--c);
    background: color-mix(in srgb, var(--c) 7%, transparent);
    border-radius: 10px;
    padding: 0.8rem 0.9rem;
  }
  .g2t-stage span.g2t-badge {
    display: inline-block;
    background: var(--c);
    color: #fff;
    font-size: 0.7rem;
    font-weight: 700;
    letter-spacing: 0.05em;
    padding: 0.1rem 0.45rem;
    border-radius: 4px;
  }
  .g2t-stage p.g2t-stage-title {
    color: var(--ct);
    font-size: 1.05rem;
    font-weight: 600;
    margin: 0.5rem 0 0.3rem;
  }
  .g2t-stage p {
    font-size: 0.9rem;
    margin: 0;
  }
  .g2t-teal {
    --c: var(--g2t-teal);
    --ct: var(--g2t-teal-text);
  }
  .g2t-purple {
    --c: var(--g2t-purple);
    --ct: var(--g2t-purple-text);
  }
  .g2t-red {
    --c: var(--g2t-red);
    --ct: var(--g2t-red-text);
  }
  .g2t-green {
    --c: var(--g2t-green);
  }
  .g2t-gait {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 0.6rem;
    margin: 0.8rem 0;
  }
  .g2t-gait figure {
    margin: 0;
  }
  .g2t-gait span.g2t-label {
    display: block;
    background: var(--c);
    color: #fff;
    font-weight: 600;
    text-align: center;
    border-radius: 4px;
    padding: 0.3rem 0;
    margin-top: 0.4rem;
  }
  .g2t-eval {
    display: grid;
    grid-template-columns: 3fr 2fr;
    gap: 1.2rem;
    align-items: center;
    margin-top: 0.8rem;
  }
  .g2t-eval figure {
    margin: 0;
  }
  .g2t-bars {
    display: grid;
    grid-template-columns: repeat(6, 1fr);
    gap: 0.4rem;
    margin-top: 0.6rem;
  }
  .g2t-bar {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .g2t-bar span.g2t-bar-val {
    font-size: 0.85rem;
    font-weight: 700;
  }
  .g2t-bar-track {
    display: flex;
    align-items: flex-end;
    width: 55%;
    height: 80px;
    border-bottom: 1px solid var(--global-divider-color);
  }
  .g2t-bar-fill {
    width: 100%;
    background: var(--g2t-teal);
    border-radius: 3px 3px 0 0;
  }
  .g2t-bar span.g2t-bar-name {
    font-size: 0.72rem;
    color: var(--global-text-color-light);
    text-align: center;
    margin-top: 0.25rem;
  }
  .g2t-stat {
    background: color-mix(in srgb, var(--g2t-teal) 7%, transparent);
    border-radius: 10px;
    padding: 1.1rem 1.2rem;
  }
  .g2t-stat p {
    margin: 0;
  }
  .g2t-stat p.g2t-stat-num {
    color: var(--g2t-teal-text);
    font-size: 3.2rem;
    font-weight: 700;
    line-height: 1;
  }
  .g2t-stat p.g2t-stat-sub {
    font-weight: 600;
    margin-bottom: 0.8rem;
  }
  .g2t-stat p.g2t-stat-title {
    color: var(--g2t-purple-text);
    font-size: 1.1rem;
    font-weight: 600;
  }
  .g2t-stat p.g2t-stat-note {
    color: var(--global-text-color-light);
    font-size: 0.85rem;
    margin-top: 0.8rem;
  }
  @media (max-width: 576px) {
    .g2t-narrow {
      max-width: 100%;
    }
    .g2t-stages,
    .g2t-eval {
      grid-template-columns: 1fr;
    }
    .g2t-gait {
      grid-template-columns: repeat(2, 1fr);
    }
  }
</style>

<p class="g2t-authors"><strong>Mo Xu</strong><sup>1</sup>, Yunfu Deng<sup>1</sup>, Jianuo Wang<sup>2</sup>, Josiah Hanna<sup>1&dagger;</sup>, Bilge Mutlu<sup>1&dagger;</sup></p>
<p class="g2t-affil"><sup>1</sup>University of Wisconsin-Madison &nbsp; <sup>2</sup>Independent Researcher &nbsp; <sup>&dagger;</sup>Joint senior authors</p>

<!-- Uncomment and fill in when the links are public:
<div class="g2t-links">
  <a class="g2t-btn" href="https://arxiv.org/abs/XXXX.XXXXX">Paper</a>
  <a class="g2t-btn" href="https://github.com/USER/REPO">Code</a>
</div>
-->

<div class="g2t-rule">
  <span style="background: var(--g2t-teal)"></span>
  <span style="background: var(--g2t-purple)"></span>
  <span style="background: var(--g2t-red)"></span>
  <span style="background: var(--g2t-green)"></span>
  <span style="background: var(--g2t-yellow)"></span>
</div>

<div class="g2t-tldr">
  <p class="g2t-tldr-head">One RL-trained policy grasps and twists open jars with a bimanual dexterous system.</p>
  <p>One hand reconfigures finger-object contacts to enable sustained lid rotation while the other hand holds the jar.</p>
</div>

## Task and Method

{% include figure.liquid loading="eager" path="assets/img/projects/grasp2twist/teaser.jpg" title="Physical system and simulation" class="img-fluid rounded z-depth-1" %}

<div class="caption">
    Physical system (left) and simulation (right). The holding hand grasps and stabilizes the jar; the twisting hand grasps and twists the lid by reconfiguring contacts.
</div>

We guide the fingers to a spatial arrangement during grasping and signal the grasp-to-twist transition.

<div class="g2t-narrow">
    {% include figure.liquid path="assets/img/projects/grasp2twist/geom_repre_simplified.png" title="Hand-object enclosure" class="img-fluid rounded" %}
</div>

We train the policy with a three-stage curriculum.

<div class="g2t-stages">
  <div class="g2t-stage g2t-teal">
    <span class="g2t-badge">STAGE 1</span>
    <p class="g2t-stage-title">Foundational skill acquisition</p>
    <p>Learn grasp acquisition and the grasp-to-twist transition.</p>
  </div>
  <div class="g2t-stage g2t-purple">
    <span class="g2t-badge">STAGE 2</span>
    <p class="g2t-stage-title">Contact reconfiguration exploration</p>
    <p>Explore finger contact changes for sustained twisting.</p>
  </div>
  <div class="g2t-stage g2t-red">
    <span class="g2t-badge">STAGE 3</span>
    <p class="g2t-stage-title">Sim-to-real adaptation</p>
    <p>Build sim-to-real robustness with domain randomization.</p>
  </div>
</div>

## Finger Gaiting in the Real World

<div class="g2t-gait">
  <div class="g2t-teal">
    {% include figure.liquid path="assets/img/projects/grasp2twist/gait_twist.jpg" title="Twist" class="img-fluid rounded" %}
    <span class="g2t-label">Twist</span>
  </div>
  <div class="g2t-red">
    {% include figure.liquid path="assets/img/projects/grasp2twist/gait_release.jpg" title="Release" class="img-fluid rounded" %}
    <span class="g2t-label">Release</span>
  </div>
  <div class="g2t-green">
    {% include figure.liquid path="assets/img/projects/grasp2twist/gait_recontact.jpg" title="Recontact" class="img-fluid rounded" %}
    <span class="g2t-label">Recontact</span>
  </div>
  <div class="g2t-purple">
    {% include figure.liquid path="assets/img/projects/grasp2twist/gait_twist_again.jpg" title="Twist again" class="img-fluid rounded" %}
    <span class="g2t-label">Twist again</span>
  </div>
</div>

Fingers release, reposition, and re-establish contact to continue twisting beyond the motion range of a fixed grasp.

## Physical Evaluation on Household Containers

<div class="g2t-eval">
  <div>
    {% include figure.liquid path="assets/img/projects/grasp2twist/containers.jpg" title="Six household containers" class="img-fluid rounded" %}
    <div class="g2t-bars">
      <div class="g2t-bar"><span class="g2t-bar-val">8/10</span><div class="g2t-bar-track"><div class="g2t-bar-fill" style="height: 80%"></div></div><span class="g2t-bar-name">Blue Peanut</span></div>
      <div class="g2t-bar"><span class="g2t-bar-val">9/10</span><div class="g2t-bar-track"><div class="g2t-bar-fill" style="height: 90%"></div></div><span class="g2t-bar-name">Yellow Mayo</span></div>
      <div class="g2t-bar"><span class="g2t-bar-val">6/10</span><div class="g2t-bar-track"><div class="g2t-bar-fill" style="height: 60%"></div></div><span class="g2t-bar-name">Pink Glass</span></div>
      <div class="g2t-bar"><span class="g2t-bar-val">10/10</span><div class="g2t-bar-track"><div class="g2t-bar-fill" style="height: 100%"></div></div><span class="g2t-bar-name">Green Vitamin</span></div>
      <div class="g2t-bar"><span class="g2t-bar-val">10/10</span><div class="g2t-bar-track"><div class="g2t-bar-fill" style="height: 100%"></div></div><span class="g2t-bar-name">Brown Peanut</span></div>
      <div class="g2t-bar"><span class="g2t-bar-val">10/10</span><div class="g2t-bar-track"><div class="g2t-bar-fill" style="height: 100%"></div></div><span class="g2t-bar-name">Instant Coffee</span></div>
    </div>
  </div>
  <div class="g2t-stat">
    <p class="g2t-stat-num">88%</p>
    <p class="g2t-stat-sub">53 / 60 trials</p>
    <p class="g2t-stat-title">Six household containers</p>
    <p>10 trials per container</p>
    <p class="g2t-stat-note">Success: complete lid thread disengagement, verified by open-loop lid lifting by the twisting hand.</p>
  </div>
</div>
