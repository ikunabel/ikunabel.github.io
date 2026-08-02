---
layout: page
title: "Sounds Like You — TUM Hackatune"
description: A recommendation UI built on Cyanite's music similarity backend
img: assets/img/cyanite_thumbnail.png
importance: 1
category: Master's
---

<i class="fa-brands fa-github"></i> [View on GitHub](https://github.com/LivanKov/mml-hackatune-26)

At TUM Hackatune, our team  built a UI on top of Cyanite's music recommendation backend that lets a user pick songs from their liked tracks and get explainable recommendations back.

Users select seed tracks from their taste profile, and Cyanite's similarity search finds matching tracks; an LLM turns Cyanite's similarity tags into a plain-language explanation of *why* each song matches. A trait-ranking and AI-summary view breaks down which similarity tags (time signature, instruments, BPM, valence/arousal, genre, vocals) matched most, and which original song features were strongly preserved, partially preserved, or neglected in the recommendations. A mood-shift map visualizes how each recommended track drifts from the liked set along axes like calm/energetic and dark/uplifting. Finally, users can refine recommendations with a free-text prompt (e.g. "but I want something more up-beat"), with prior queries aggregated to keep guiding the recommendations toward the user's preference.

<style>
  .slideshow { position: relative; margin-top: 1rem; padding: 0 3rem; }
  .slideshow-track { position: relative; }
  .slideshow .slide { display: none; text-align: center; }
  .slideshow .slide.active { display: block; }
  .slideshow .slide-caption { margin-top: 0.5rem; color: var(--global-text-color-light, #666); }
  .slideshow-arrow {
    position: absolute; top: 50%; transform: translateY(-50%);
    background: none; border: none; cursor: pointer; color: inherit;
    font-size: 2rem; line-height: 1; padding: 0.25rem 0.5rem; opacity: 0.6;
    transition: opacity 120ms ease, color 120ms ease;
  }
  .slideshow-arrow:hover { opacity: 1; color: var(--global-theme-color); }
  .slideshow-prev { left: -3rem; }
  .slideshow-next { right: -3rem; }
  .slideshow-dots { display: flex; justify-content: center; gap: 6px; margin-top: 0.75rem; }
  .slideshow-dots button { width: 9px; height: 9px; padding: 0; border-radius: 50%; border: 1px solid var(--global-divider-color, #ccc); background: transparent; }
  .slideshow-dots button.active { background: var(--global-theme-color); border-color: var(--global-theme-color); }
</style>

<div class="slideshow" id="cyanite-slideshow">
  <div class="slideshow-track">
    <button type="button" class="slideshow-arrow slideshow-prev" aria-label="Previous slide">&larr;</button>
    <button type="button" class="slideshow-arrow slideshow-next" aria-label="Next slide">&rarr;</button>

    <div class="slide active">
      {% include figure.liquid loading="eager" path="assets/img/cyanite3.png" title="Select songs from user's taste profile" class="img-fluid rounded z-depth-1" zoomable=true %}
      <p class="slide-caption">Select songs from user's taste profile</p>
    </div>
    <div class="slide">
      {% include figure.liquid loading="eager" path="assets/img/cyanite4.png" title="Cyanite similarity search and LLM explanations" class="img-fluid rounded z-depth-1" zoomable=true %}
      <p class="slide-caption">Cyanite similarity search and LLM explanations</p>
    </div>
    <div class="slide">
      {% include figure.liquid loading="eager" path="assets/img/cyanite5.png" title="Trait ranking and preserved-features summary" class="img-fluid rounded z-depth-1" zoomable=true %}
      <p class="slide-caption">Trait ranking and preserved-features summary</p>
    </div>
    <div class="slide">
      {% include figure.liquid loading="eager" path="assets/img/cyanite6.png" title="Map similar songs by mood shift" class="img-fluid rounded z-depth-1" zoomable=true %}
      <p class="slide-caption">Map similar songs by mood shift</p>
    </div>
    <div class="slide">
      {% include figure.liquid loading="eager" path="assets/img/cyanite7.png" title="Refine recommendations with a prompt" class="img-fluid rounded z-depth-1" zoomable=true %}
      <p class="slide-caption">Refine recommendations with a prompt</p>
    </div>
  </div>

  <div class="slideshow-dots"></div>
</div>

<script>
  (function () {
    var root = document.getElementById('cyanite-slideshow');
    var slides = root.querySelectorAll('.slide');
    var dotsWrap = root.querySelector('.slideshow-dots');
    var current = 0;

    slides.forEach(function (_, i) {
      var dot = document.createElement('button');
      dot.type = 'button';
      dot.setAttribute('aria-label', 'Go to slide ' + (i + 1));
      if (i === 0) dot.classList.add('active');
      dot.addEventListener('click', function () { show(i); });
      dotsWrap.appendChild(dot);
    });
    var dots = dotsWrap.querySelectorAll('button');

    function show(i) {
      current = (i + slides.length) % slides.length;
      slides.forEach(function (s, j) { s.classList.toggle('active', j === current); });
      dots.forEach(function (d, j) { d.classList.toggle('active', j === current); });
    }

    root.querySelector('.slideshow-prev').addEventListener('click', function () { show(current - 1); });
    root.querySelector('.slideshow-next').addEventListener('click', function () { show(current + 1); });
  })();
</script>
