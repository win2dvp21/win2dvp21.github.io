---
layout: default
title: About
permalink: /
subtitle: Research Intern, Korea Institute of Science and Technology (KIST)
portrait_image: /assets/img/seungyoun.jpg
cat_image: /assets/img/kinyangi.jpg
---

<!-- Keep these styles in the page body so the default layout renders them. -->
<style>
  .about-page .about-hero,
  .about-page .about-personal {
    display: grid;
    grid-template-columns: minmax(0, 1fr) 200px;
    align-items: start;
    gap: 2rem;
  }
  .about-page .about-hero {
    margin-bottom: 1.5rem;
  }
  .about-page .about-hero-text,
  .about-page .about-personal-text {
    min-width: 0;
  }
  .about-page .post-header {
    margin-bottom: 1rem;
  }
  .about-page .post-title {
    margin-top: 0;
  }
  .about-page .about-portrait,
  .about-page .about-cat {
    width: 200px;
    max-width: 100%;
    margin: 0;
  }
  .about-page .about-portrait img,
  .about-page .about-cat img {
    display: block;
    border-radius: 6px;
  }
  .about-page .about-cat figcaption {
    margin-top: 0.4rem;
    text-align: center;
    font-size: 0.85rem;
    line-height: 1.4;
  }
  .about-page .about-personal h2 {
    margin-top: 0;
  }
  .about-page .about-personal {
    margin-top: 1.5rem;
  }
  @media (max-width: 575.98px) {
    .about-page .about-hero,
    .about-page .about-personal {
      grid-template-columns: minmax(0, 1fr);
      gap: 1rem;
    }
    .about-page .about-portrait {
      width: 144px;
    }
    .about-page .about-cat {
      width: 200px;
    }
  }
</style>

<div class="post about-page">
  <div class="about-hero">
    <div class="about-hero-text">
      <header class="post-header">
        <h1 class="post-title">{{ site.first_name | escape }} {{ site.last_name | escape }}</h1>
        <p class="desc">{{ page.subtitle | escape }}</p>
      </header>
      <p>
        <a href="mailto:seungyoun.syl@gmail.com">Email</a> ·
        <a href="https://github.com/win2dvp21">GitHub</a> ·
        <a href="https://www.linkedin.com/in/seungyounlee/">LinkedIn</a>
      </p>
      <p>
        I completed my M.S. in Artificial Intelligence at Korea University and now work
        as a research intern in the Computational Brain &amp; Intelligence Laboratory at KIST.
        My interests lie at the intersection of neuroscience and artificial intelligence.
        I want to understand the neural computations underlying learning and information
        processing, and explore what they can teach us about artificial intelligence.
      </p>
      <p>
        My master's research used biophysical models of auditory and visual cortical
        circuits to study how disinhibition shapes information transmission. I have also
        worked on safety alignment for medical large language models.
      </p>
    </div>
    <figure class="about-portrait">
      <img src="{{ page.portrait_image | relative_url }}" alt="Seungyoun Lee with a robot" width="200" height="300" style="width: 100%; max-width: 200px; height: auto;" loading="eager" decoding="async">
    </figure>
  </div>

  <h2 id="education-training">Education</h2>
  <ul>
    <li>
      <p><strong>Korea University</strong> · 2024–2026<br>
      M.S. in Artificial Intelligence, Korea University–KIST Cooperative Graduate Program.</p>
    </li>
    <li>
      <p><strong>Carnegie Mellon University</strong> · 2025–2026<br>
      Visiting Student, Intensive AI Program sponsored by the Korean government.<br>
      <strong>Ranked 1st in the 25-participant cohort.</strong></p>
    </li>
    <li>
      <p><strong>Ewha Womans University</strong> · 2018–2024<br>
      B.S. in Computer Science and Engineering and Brain &amp; Cognitive Sciences (double major).<br>
      Graduated <strong>magna cum laude</strong>.</p>
    </li>
  </ul>

  <h2 id="selected-honors">Honors, Fellowships &amp; Awards</h2>
  <ul>
    <li>
      <p><strong>Presidential Science Scholarship for Graduate Students</strong>, Korea Student Aid Foundation · Mar. 2024–Aug. 2026<br>
      One of 25 first-year master's students nationwide to receive full funding for the degree.<br>
      <a href="https://www.asiatime.co.kr/article/20240523500260">News coverage (Korean)</a></p>
    </li>
    <li>
      <p><strong>Outstanding Graduate Award</strong>, KIST Academic–Research Cooperative Program · Aug. 2026<br>
      Selected as one of two master's graduates recognized institute-wide.</p>
    </li>
    <li>Excellence Award, Poster Presentation, Conference on Electronics, Semiconductor, and AI · Aug. 2025</li>
    <li>Excellence Award, Project Presentation, Computational Neuroscience Winter School · Feb. 2025</li>
    <li>Special Award – Hugging Face OSS Team, Open-Source Contribution Academy · Dec. 2024</li>
    <li>1st Place, GenAI Hands-on Challenge, AWS × Girls in Tech Korea · Dec. 2023</li>
    <li>SW Future Competence Development Scholarship, Ewha Womans University · Dec. 2023</li>
    <li>Encouragement Award, International Capstone Design Fair, Korea University · Nov. 2023</li>
    <li>Ewha Discovery &amp; Adventure Lab Scholarship, Ewha Womans University · Jun. 2023</li>
    <li>Finalist, 5th Open Infra Development Competition, Mentech · May 2023</li>
    <li>Honorable Mention, Solana Grizzlython, Solana Foundation · Apr. 2023</li>
    <li>4th Place, Ewha Power ProgrammER Competition · Oct. 2022</li>
  </ul>

  <div class="about-personal">
    <div class="about-personal-text">
      <h2 id="outside-the-lab">Outside the Lab</h2>
      <p>
        I love listening to music.
        <a href="https://youtu.be/DPJL488cfRw">Yunchan Lim's performance of Rachmaninoff's Piano Concerto No. 3</a>
        is a particular favorite, and lately I've also been listening to a lot of <a href="https://youtu.be/GTIeVJh1Fvo">Laufey</a>.
      </p>
      <p>I also enjoy spending time with Kinyangi (키냥이), a well-known cat at KIST.</p>
    </div>
    <figure class="about-cat">
      <img src="{{ page.cat_image | relative_url }}" alt="Kinyangi, a cat at KIST" width="200" height="113" style="width: 100%; max-width: 200px; height: auto;" loading="lazy" decoding="async">
      <figcaption>My best shot of Kinyangi.</figcaption>
    </figure>
  </div>
</div>
