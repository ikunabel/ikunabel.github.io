<div style="max-width: 2000px; margin: 0 auto; padding-left: 20px; padding-right: 20px;">

  <style>
    html { scroll-behavior: smooth; }
    .top-nav {
      position: sticky; top: 0; z-index: 1000;
      background: #ffffffcc; backdrop-filter: saturate(180%) blur(10px);
      border-bottom: 1px solid #eaecef; padding: 8px 12px; margin: 0 -20px 80px -20px;
      box-shadow: 0 2px 12px rgba(0,0,0,0.06);
    }
    .top-nav-inner { 
      display: flex; gap: 8px; flex-wrap: nowrap; align-items: center; justify-content: center; 
      max-width: 980px; margin: 0 auto; padding: 6px 4px; overflow-x: auto;
      -webkit-overflow-scrolling: touch;
    }
    .top-nav-inner::-webkit-scrollbar { height: 6px; }
    .top-nav-inner::-webkit-scrollbar-thumb { background: #d0d7de; border-radius: 4px; }
    .top-nav a { 
      color: #0366d6; text-decoration: none; font-weight: 600; font-size: 0.95rem;
      padding: 8px 12px; border-radius: 9999px; border: 1px solid transparent;
      transition: background-color 120ms ease, color 120ms ease, border-color 120ms ease;
      white-space: nowrap;
    }
    .top-nav a:hover { background: #f0f7ff; border-color: #cde0ff; }
    .top-nav a:focus { outline: 2px solid #9ec5ff; outline-offset: 2px; }

    /* News cards */
    .news-grid { display: grid; grid-template-columns: 1fr; gap: 12px; }
    .news-card {
      background: #fff; border: 1px solid #eee; border-radius: 12px; padding: 12px 14px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.06); transition: transform 160ms ease, box-shadow 160ms ease;
      display: block;
    }
    .news-card:hover { transform: translateY(-3px); box-shadow: 0 10px 20px rgba(0,0,0,0.12); }
    .news-date {
      color: #ff6b89; font-weight: 700; font-size: 0.9rem; display: block; margin-bottom: 4px;
    }
    .news-body { line-height: 1.5; }

    /* Projects grid */
    .project-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 16px;
    }
    .project-card {
      background: #fff;
      border: 1px solid #eee;
      border-radius: 12px;
      padding: 16px 18px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.06);
      transition: transform 160ms ease, box-shadow 160ms ease;
      display: block;
    }
    .project-card:hover {
      transform: translateY(-4px);
      box-shadow: 0 10px 20px rgba(0,0,0,0.12);
    }
    .project-card h3 { margin-top: 0; }
    .project-card img { max-width: 100%; height: auto; border-radius: 8px; }

    /* Education grid */
    .edu-grid {
      display: grid;
      grid-template-columns: 1fr; /* stack cards vertically, full width */
      gap: 16px;
    }
    .edu-card {
      background: #fff;
      border: 1px solid #eee;
      border-radius: 12px;
      padding: 16px 18px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.06);
      transition: transform 160ms ease, box-shadow 160ms ease;
      display: flex; align-items: center; gap: 14px;
    }
    .edu-card:hover {
      transform: translateY(-4px);
      box-shadow: 0 10px 20px rgba(0,0,0,0.12);
    }
    .edu-card h3 { margin-top: 0; margin-bottom: 6px; }
    .edu-card img { width: 84px; height: auto; border-radius: 6px; flex-shrink: 0; }
    .edu-body { flex: 1; }

    @media (max-width: 520px) {
      .edu-card { flex-direction: column; align-items: flex-start; }
      .edu-card img { width: 72px; }
    }

    /* Work Experience cards */
    .work-grid {
      display: grid;
      grid-template-columns: 1fr; /* stack for wide, horizontal cards */
      gap: 16px;
    }
    .work-card {
      background: #fff;
      border: 1px solid #eee;
      border-radius: 12px;
      padding: 16px 18px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.06);
      transition: transform 160ms ease, box-shadow 160ms ease;
      display: flex; align-items: center; gap: 14px;
    }
    .work-card:hover { transform: translateY(-4px); box-shadow: 0 10px 20px rgba(0,0,0,0.12); }
    .work-body { flex: 1; }
    .work-card h3 { margin: 0 0 6px 0; }
    @media (max-width: 520px) { .work-card { flex-direction: column; align-items: flex-start; } }
    /* grid remains single-column across breakpoints to keep cards wide */

    /* Responsive YouTube embeds */
    .video-embed { position: relative; width: 100%; aspect-ratio: 16 / 9; margin-top: 8px; }
    .video-embed iframe { position: absolute; inset: 0; width: 100%; height: 100%; border: 0; border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.1); }

    /* Thumbnail fallback for blocked embeds */
    .video-thumb { position: relative; width: 100%; aspect-ratio: 16 / 9; margin-top: 8px; border-radius: 8px; overflow: hidden; box-shadow: 0 4px 12px rgba(0,0,0,0.1); background: #000; display: block; }
    .video-thumb img { width: 100%; height: 100%; object-fit: cover; display: block; }
    .video-thumb::after { content: '▶'; position: absolute; left: 50%; top: 50%; transform: translate(-50%, -50%); color: #fff; font-size: 28px; line-height: 1; background: rgba(0,0,0,0.45); width: 64px; height: 64px; border-radius: 50%; display: grid; place-items: center; }
    .video-thumb:hover::after { background: rgba(0,0,0,0.6); }

    /* Perfect circular profile avatar */
    .profile-photo { width: 220px; aspect-ratio: 1 / 1; border-radius: 50%; overflow: hidden; box-shadow: 0 4px 8px rgba(0,0,0,0.1); flex-shrink: 0; }
    .profile-photo img { width: 100%; height: 100%; object-fit: cover; display: block; object-position: 50% calc(50% + 20px); }

    /* Performance tiles */
    .perf-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(320px, 1fr)); gap: 16px; }
    .perf-card { background: #fff; border: 1px solid #eee; border-radius: 12px; padding: 14px 16px; box-shadow: 0 2px 8px rgba(0,0,0,0.06); transition: transform 160ms ease, box-shadow 160ms ease; }
    .perf-card:hover { transform: translateY(-4px); box-shadow: 0 10px 20px rgba(0,0,0,0.12); }
    .perf-card h3 { margin: 0 0 6px 0; font-size: 1.05rem; }

    /* Make the Jekyll (Cayman) header much shorter */
    .page-header {
      padding-top: 16px !important;
      padding-bottom: 16px !important;
      min-height: 0 !important;
    }
    .page-header .project-name { font-size: 2.4rem !important; }
    .page-header .project-tagline { font-size: 1.2rem !important; }
  </style>

  <nav class="top-nav">
    <div class="top-nav-inner">
      <a href="#news">News</a>
      <a href="#projects">Projects</a>
      <a href="#work-experience">Work</a>
      <a href="#education">Education</a>
      <a href="#performances">Performances</a>
      <a href="#interests">Interests</a>
      <a href="#friends">Check out my friends</a>
    </div>
  </nav>

  <div style="display: flex; align-items: flex-start; gap: 20px; margin-bottom: 2em;">
    <div class="profile-photo">
      <img src="{{ '/assets/images/DSC_4601_Bewerbung_uncrop_3.jpg' | relative_url }}" alt="Ábel Ilyés-Kun" />
    </div>
    <div style="margin-left: 20px;">
      <p>
        I am Ábel, a computer science graduate from RWTH Aachen University.
        My academic interests include AI for music generation, natural language processing, and computational neuroscience.
        Beyond my studies, I am passionate about playing the piano and enjoy transcribing recordings from my favorite musicians,
        Brad Mehldau and Chick Corea.
        <br/><br/>
        <a href="mailto:ikunabel@gmail.com">Email</a> |
        <a href="https://github.com/ikunabel" target="_blank">GitHub</a> |
        <a href="https://scholar.google.com/citations?hl=en&user=jX1zoasAAAAJ" target="_blank">Google Scholar</a> |
        <a href="https://www.linkedin.com/in/%C3%A1bel-ily%C3%A9s-kun-6350a3245/" target="_blank">LinkedIn</a> |
        <a href="{{ '/assets/docs/CV_Abel_2026_Jan_9.pdf' | relative_url }}" target="_blank">CV</a>
      </p>  
    </div>
  </div>

  <div style="max-width: 900px; margin: 0 auto;">

      <h1 id="news" style="scroll-margin-top: 80px;">News</h1>
      <div class="news-grid">
        <div class="news-card">
          <div class="news-date">[October 2025]</div>
          <div class="news-body">I will begin my master' thesis on real-time human-AI cooperative improvisation at the <a href="https://www.aim.rwth-aachen.de/" target="_blank">Chair for Artificial Intelligence Methodology (AIM)</a> at RWTH Aachen.</div>
        </div>

        <div class="news-card">
          <div class="news-date">[September 2025]</div>
          <div class="news-body">My co-authored paper <a href="https://arxiv.org/abs/2511.07268" target="_blank">"Generating Piano Music with Transformers: A Comparative Study of Scale, Data and Metrics"</a> was accepted at the <a href="https://aiformusicworkshop.github.io/" target="_blank">NeurIPS 2025 Workshop on AI for Music</a>!</div>
        </div>

        <div class="news-card">
          <div class="news-date">[September 2024]</div>
          <div class="news-body">I started my exchange semester at the Korean Advanced Institute of Science and Technology (KAIST) and received the DUO-Korea scholarship.</div>
        </div>
      </div>


  <h1 id="projects" style="scroll-margin-top: 80px;">Research and Projects</h1>

      <div class="project-grid">
        <div class="project-card">
          <h3>🎹 Real-time Human-AI Improvisation over Jazz Standards</h3>
          <p><em>Fall 2025</em></p>
          <p>
            I am currently pursuing my master’s thesis at the Chair for Artificial Intelligence Methodology at RWTH Aachen, exploring real-time human-AI musical interaction on a "Yamaha Disklavier" MIDI keyboard. The goal is to fine-tune a chord accompaniment agent with reinforcement learning to generate musically sensible chords in response to a melody played by a human performer. The system aims to enable engaging jam sessions over jazz standards by reharmonizing the performer’s melody and offering multiple harmonic alternatives through an interactive user interface.
          </p>
        </div>

        <div class="project-card">
          <h3>🎹 Generating Piano Music with Transformers: A Comparative Study of Scale, Data and Metrics</h3>
          <p><em>Summer 2025</em></p>
          <p>
            <img src="{{ '/assets/images/Confusion_Matrix.png' | relative_url }}" alt="Confusion Matrix" width="250"/>
          </p>
          <p>
            As part of a university lab project, I worked on generating MIDI piano performances with Transformers. We systematically compared different datasets, model architectures, model sizes, and training strategies to evaluate their impact on generative quality. To support model development and evaluation, we examined a range of quantitative metrics and analyzed how well they correlate with human judgment collected through listening studies. Our best-performing model, a 950M-parameter transformer trained on 80K MIDI files from diverse genres, produces outputs that are often rated as human-composed in a Turing-style listening survey.
          </p>
        </div>

        <div class="project-card">
          <h3>VR Game for Learning Git</h3>
          <p><em>Summer 2025</em></p>
          <p>
            <img src="{{ '/assets/images/Git_Immersive_Learning_Presentation.png' | relative_url }}" alt="VR_Git" width="350"/>
          </p>
          <p>
            I co-developed a 3D VR game in Unity to teach git in an interactive, hands-on environment. Branches are represented as color-coded shelves, and files as items that can be put on the shelves (e.g., cubes for .py, books for .docx), allowing students to visualize and experiment with core git commands like add, commit, merge, and push. The user can trigger git commands from a UI panel with the VR controller and observe the effect in the immersive environment. The game provides a risk-free space to build mental models, reinforce correct workflows, and reduce fear of mistakes, preparing learners for real-world git projects.
          </p>
        </div>

        <div class="project-card">
          <h3>Mamba State-space Model</h3>
          <p><em>Summer 2024</em></p>
          <p>
            Over the past summer at my home university, I participated in a research seminar at the Machine Learning and Reasoning chair involving Mamba, a recent state-space model. The experience sparked my interest in continuing to explore state-space models on music data. Since Mamba-variants can process extremely long sequences more efficiently than Transformers, it can be interesting to see how they handle long temporal dependencies in music data.
          </p>
        </div>

        <div class="project-card">
          <h3>Bachelor's Thesis at Institute for Computational and Systems Neuroscience</h3>
          <p><em>October 2022 – May 2023</em></p>
          <p>
            The goal for this project was to optimize the hyper-parameters of a spiking neural network model with Optuna. The work involved parallel computation on the JURECA cluster and experimentation with sampling algorithms (TPE, random).
          </p>
        </div>

        <div class="project-card">
          <h3>🚙 Lab Course at Cyber-Physical Mobility Lab</h3>
          <p><em>October 2021 – February 2022</em></p>
          <p>
            My group implemented trajectory planning and collision avoidance for model vehicles in C++. The workflow was organized in team of six with Scrum and Git.
          </p>
        </div>

        <div class="project-card">
          <h3>🎵 Computer-generated Music</h3>
          <p><em>Summer 2020</em></p>
          <p>
            During my bachelor's degree at RWTH Aachen University, I did a seminar on computer-generated music, where I covered recent neural-network-based approaches like Google Magenta or the Bachbot, also discussing the LZ compression algorithm within the OpenMusic software.
          </p>
        </div>
      </div>


      <br/><br/>


      <h1 id="work-experience" style="scroll-margin-top: 80px;">Work Experience</h1>

      <div class="work-grid">
        <div class="work-card">
          <div class="work-body">
            <h3>Tutor at Research Group for Programming Languages and Verification</h3>
            <p><em>October 2021 – March 2022, October 2022 – March 2023</em></p>
            <p>
              I tutored students in Software Development (Java), Functional Programming (Haskell), Logic Programming (Prolog) and software verification, conducted weekly classes and assessed coding assignments.
            </p>
          </div>
        </div>

        <div class="work-card">
          <div class="work-body">
            <h3>Internship at BWI GmbH</h3>
            <p><em>March 2020</em></p>
            <p>
              I was introduced to current JIRA projects and gained an overview of project management and project organization in Scrum.
            </p>
          </div>
        </div>
      </div>


      <br/><br/>


      <h1 id="education" style="scroll-margin-top: 80px;">Education</h1>

      <div class="edu-grid">
        <div class="edu-card">
          <img src="{{ '/assets/images/RWTH_Logo_3.svg.png' | relative_url }}" alt="RWTH Logo" />
          <div class="edu-body">
            <h3>RWTH Aachen University</h3>
            <p>MSc Computer Science</p>
            <p><em>October 2023 – Present</em></p>
          </div>
        </div>

        <div class="edu-card">
          <img src="{{ '/assets/images/KAIST_logo.png' | relative_url }}" alt="KAIST Logo" />
          <div class="edu-body">
            <h3>KAIST</h3>
            <p>MSc Computer Science Exchange</p>
            <p><em>September 2024 – December 2024</em></p>
            <p>Received DUO-Korea Scholarship</p>
          </div>
        </div>

        <div class="edu-card">
          <img src="{{ '/assets/images/RWTH_Logo_3.svg.png' | relative_url }}" alt="RWTH Logo" />
          <div class="edu-body">
            <h3>RWTH Aachen University</h3>
            <p>BSc Computer Science</p>
            <p><em>October 2019 – June 2023</em></p>
          </div>
        </div>

        <div class="edu-card">
          <div class="edu-body">
            <h3>Goethe Gymnasium Bad Ems</h3>
            <p>A levels (Abitur)</p>
            <p>Majors: English, Mathematics, Physics</p>
            <p>DPG Abitur Prize in Physics</p>
          </div>
        </div>
      </div>

      <br/><br/>

      <h1 id="stack" style="scroll-margin-top: 80px;">Programming Stack</h1>

      <p><strong>Main Languages</strong><br/>
      Python, Java</p>

      <p><strong>Project Experience in</strong><br/>
      Bash, C, C++, C#, SQL</p>

      <p><strong>Frameworks</strong><br/>
      PyTorch, Librosa, NumPy, SciPy, Pandas, Matplotlib, Seaborn</p>

      <p><strong>Tools &amp; Systems</strong><br/>
      Linux, Git, Slurm, Jupyter, Unity</p>


      <br/><br/>


      <h1 id="performances" style="scroll-margin-top: 80px;">Performances</h1>
      <p>
        During my exchange semester at KAIST, I joined “창작동화” Jazz Band as a keyboardist. We
        performed at multiple campus events and had a featured performance at a jazz bar in Seoul.
        Here are a couple of recordings:
      </p>
      <div class="perf-grid">
        <div class="perf-card">
          <h3>Cafe Dream performance</h3>
          <a class="video-thumb" href="https://www.youtube.com/watch?v=KJfYqBJzVuc" target="_blank" rel="noopener" aria-label="Open Cafe Dream performance on YouTube in a new tab">
            <img src="https://img.youtube.com/vi/KJfYqBJzVuc/hqdefault.jpg" alt="Cafe Dream performance thumbnail" loading="lazy"/>
          </a>
          <p>I played “Beautiful Love”.</p>
        </div>
        <div class="perf-card">
          <h3>KAIST winter performance</h3>
          <a class="video-thumb" href="https://www.youtube.com/watch?v=9AuTRtL2spo" target="_blank" rel="noopener" aria-label="Open KAIST winter performance on YouTube in a new tab">
            <img src="https://img.youtube.com/vi/9AuTRtL2spo/hqdefault.jpg" alt="KAIST winter performance thumbnail" loading="lazy"/>
          </a>
          <p>I played “Spain”, “How Deep Is the Ocean?”, and “September”. I also edited and color-graded the video.</p>
        </div>
      </div>


      <br/><br/>


      <h1 id="interests" style="scroll-margin-top: 80px;">Interests</h1>
      <p>Jazz piano, classical piano, transcribing music, K-pop, video editing, psychology,
        football, table tennis, tennis, running
      </p>

      <br/><br/>

      <h1 id="friends" style="scroll-margin-top: 80px;">Check out my friends</h1>
      <p>Meet my mentor <a href="https://yuanjiayiy.github.io/" target="_blank" rel="noopener">Carrie Yuan</a>.</p>

  </div>
</div>
