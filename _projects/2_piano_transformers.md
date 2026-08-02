---
layout: page
title: "Generating Piano Music with Transformers"
description: A study of how model scale, datasets, training strategies and metrics affect symbolic piano music generation.
img: assets/img/Confusion_Matrix.png
importance: 2
category: Master's
---

<i class="fa-brands fa-github"></i> [View on GitHub](https://github.com/kaanozaltan/piano-transformer)

<i class="fa-solid fa-music"></i> [Check out for music samples here!](https://drive.google.com/drive/folders/1F_HzY3lxXqOzP_PXCYyZM_5SipklndYb)

As part of a university lab project, I worked on generating MIDI piano performances with Transformers. We systematically compared different datasets, model architectures, model sizes, and training strategies to evaluate their impact on generative quality. To support model development and evaluation, we examined a range of quantitative metrics and analyzed how well they correlate with human judgment collected through listening studies. Our best-performing model, a 950M-parameter transformer trained on 80K MIDI files from diverse genres, produces outputs that are often rated as human-composed in a Turing-style listening survey.

Our poster:

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/piano_transformers_poster.png" title="AI4Music Poster" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
