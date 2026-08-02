---
layout: page
title: Real-time Human-AI Improvisation over Jazz Standards
description: Master's thesis at the Chair for AI Methodology, RWTH Aachen
img: assets/img/kawai_realjam.jpg
importance: 0
category: Master's
---

<i class="fa-brands fa-github"></i> [View on GitHub](https://github.com/ikunabel/realchords-pytorch)

I am currently pursuing my master's thesis at the Chair for Artificial Intelligence Methodology at RWTH Aachen, exploring real-time human-AI musical interaction on a Yamaha Disklavier MIDI keyboard. The goal is to fine-tune a chord accompaniment agent with reinforcement learning to generate musically sensible chords in response to a melody played by a human performer.

My project proposes methodological extensions to the lineage of work: [Adaptive Accompaniment with ReaLchords](https://arxiv.org/abs/2506.14723) (Wu et al., 2024), [ReaLJam: Real-Time Human-AI Music Jamming with Reinforcement Learning-Tuned Transformers](https://arxiv.org/abs/2502.21267) (Scarlatos et al., 2025), and [Generative Adversarial Post-Training Mitigates Reward Hacking in Live Human-AI Music Interaction](https://arxiv.org/abs/2511.17879) (Wu et al., 2025). I reproduced the results from these papers serve as a baseline.

**Data.** The original training mix covered four datasets (Hooktheory, POP909, Nottingham, Wikifonia). I added converters for five more — the Chord Melody Dataset and JAZZMUS (popular tunes and jazz standards), EMOPIA+ (emotion-labeled pop piano), and WJD and FiloBass (jazz solos over with walking bass) — pulling in different harmonic vocabularies rather than just more pop/rock.

**Multi-scale reward.** I trained reward models that score chord-melody coherence over fixed and sliding windows at several time scales (16 to 128 frames), to see whether reward signal at a finer granularity than the whole clip helps RL training pick up local phrasing rather than only global style.

**Voicing extraction.** I built a pipeline that mines real simultaneous note-onsets from vast MIDI corpora (Aria-MIDI and Jazzvar) and maps them back to chord symbols, to eventually give the model a lookup table of real voicings instead of a simple block voicing per chord.

**Evaluation.** I extended the original benchmark suite with a metric that scores whether the melody notes played over a chord are in the right mode.

**Next up:** Ablations — does the added data diversity actually improve chord quality (not just avoid overfitting one corpus), do the multi-scale rewards outperform single-scale ones once plugged into RL, and how sensitive is the whole pipeline to the per-dataset sampling weights.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/kawai_realjam.jpg" title="Real-time Human-AI Improvisation" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
