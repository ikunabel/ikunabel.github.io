---
layout: page
title: music
permalink: /music/
description: Performances and compositions.
nav: true
nav_order: 6
---

During my exchange semester at KAIST, I joined "창작동화" Jazz Band as a keyboardist. We performed at multiple campus events and had a featured performance at a jazz bar in Seoul. In my freetime, I like to practice improvisation and sometimes I try to compose short pieces.

<style>
  .video-embed { position: relative; width: 100%; aspect-ratio: 16 / 9; }
  .video-embed iframe { position: absolute; inset: 0; width: 100%; height: 100%; border: 0; }

  .video-thumb { position: relative; width: 100%; aspect-ratio: 16 / 9; overflow: hidden; background: #000; display: block; cursor: pointer; }
  .video-thumb img { width: 100%; height: 100%; object-fit: cover; display: block; }
  .video-thumb::after { content: '▶'; position: absolute; left: 50%; top: 50%; transform: translate(-50%, -50%); color: #fff; font-size: 28px; line-height: 1; background: rgba(0,0,0,0.45); width: 64px; height: 64px; border-radius: 50%; display: grid; place-items: center; }
  .video-thumb:hover::after { background: rgba(0,0,0,0.6); }
</style>

<div class="projects">
  <div class="row row-cols-1 row-cols-md-3">
    <div class="col">
      <div class="card h-100 hoverable">
        <div class="video-thumb" data-yt-id="KJfYqBJzVuc" role="button" tabindex="0" aria-label="Play Cafe Dream performance">
          <img src="https://img.youtube.com/vi/KJfYqBJzVuc/hqdefault.jpg" alt="Cafe Dream performance thumbnail" loading="lazy"/>
        </div>
        <div class="card-body">
          <h2 class="card-title">Cafe Dream performance</h2>
          <p class="card-text">I played "Beautiful Love".</p>
        </div>
      </div>
    </div>
    <div class="col">
      <div class="card h-100 hoverable">
        <div class="video-thumb" data-yt-id="9AuTRtL2spo" role="button" tabindex="0" aria-label="Play KAIST winter performance">
          <img src="https://img.youtube.com/vi/9AuTRtL2spo/hqdefault.jpg" alt="KAIST winter performance thumbnail" loading="lazy"/>
        </div>
        <div class="card-body">
          <h2 class="card-title">KAIST winter performance</h2>
          <p class="card-text">I played "Spain", "How Deep Is the Ocean?", and "September". I also edited and color-graded the video.</p>
        </div>
      </div>
    </div>
    <div class="col">
      <div class="card h-100 hoverable">
        <div class="video-thumb" data-yt-id="WqgTwSP7Ezk" role="button" tabindex="0" aria-label="Play performance video">
          <img src="https://img.youtube.com/vi/WqgTwSP7Ezk/hqdefault.jpg" alt="A short composition thumbnail" loading="lazy"/>
        </div>
        <div class="card-body">
          <h2 class="card-title">Composition</h2>
          <p class="card-text">I composed a short piece starting with two voices that form a 2-5-1 progression and gradually becoming more free and jazzy.</p>
        </div>
      </div>
    </div>
  </div>
</div>

<script>
  document.querySelectorAll('.video-thumb[data-yt-id]').forEach(function (el) {
    function play() {
      var id = el.getAttribute('data-yt-id');
      var wrap = document.createElement('div');
      wrap.className = 'video-embed';
      var iframe = document.createElement('iframe');
      iframe.src = 'https://www.youtube.com/embed/' + id + '?autoplay=1';
      iframe.title = 'YouTube video player';
      iframe.setAttribute('allow', 'accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share');
      iframe.allowFullscreen = true;
      wrap.appendChild(iframe);
      el.replaceWith(wrap);
    }
    el.addEventListener('click', play);
    el.addEventListener('keydown', function (e) {
      if (e.key === 'Enter' || e.key === ' ') { e.preventDefault(); play(); }
    });
  });
</script>
