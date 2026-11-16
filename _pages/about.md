---
layout: about
title: About
permalink: /
subtitle: Research Intern, Korea Institute of Science and Technology (KIST)

# Images are rendered below only after their files have been uploaded.
profile: false
portrait_image: /assets/img/seungyoun.jpg
cat_image: /assets/img/kinyangi.jpg

selected_papers: false

# Contact links are written directly below.
social: false

announcements:
  enabled: false

latest_posts:
  enabled: false

_styles: |
  .about-portrait {
    float: right;
    width: 200px;
    max-width: 40%;
    margin: 0 0 1rem 1.5rem;
  }
  .about-portrait img,
  .about-cat img {
    display: block;
    width: 100%;
    height: auto;
    border-radius: 6px;
  }
  .about-clear {
    clear: both;
  }
  .about-personal {
    display: flex;
    align-items: flex-start;
    gap: 1.5rem;
  }
  .about-personal-text {
    flex: 1;
    min-width: 0;
  }
  .about-cat {
    flex: 0 0 220px;
    width: 220px;
    max-width: 100%;
    margin: 0;
  }
  .about-cat figcaption {
    margin-top: 0.4rem;
    text-align: center;
    font-size: 0.85rem;
  }
  @media (max-width: 575.98px) {
    .about-portrait {
      float: none;
      width: 144px;
      max-width: 100%;
      margin: 0 auto 1rem;
    }
    .about-personal {
      display: block;
    }
    .about-cat {
      margin-top: 1rem;
    }
  }
---

{% assign portrait = site.static_files | where: "path", page.portrait_image | first %}
{% if portrait %}
<figure class="about-portrait">
  <img src="{{ page.portrait_image | relative_url }}" alt="Seungyoun Lee with a robot" width="1024" height="1536" loading="eager" decoding="async">
</figure>
{% endif %}

[Email](mailto:seungyoun.syl@gmail.com) · [GitHub](https://github.com/win2dvp21) · [LinkedIn](https://www.linkedin.com/in/seungyounlee/)

I completed my M.S. in Artificial Intelligence at Korea University and now work
as a research intern in the Computational Brain & Intelligence Laboratory at KIST.
My interests lie at the intersection of neuroscience and artificial intelligence.
I want to understand the neural computations underlying learning and information
processing, and explore what they can teach us about artificial intelligence.

My master's research used biophysical models of auditory and visual cortical
circuits to study how disinhibition shapes information transmission. I have also
worked on safety alignment for medical large language models.

<div class="about-clear"></div>

## Education & Training

- **Korea University** · 2024–2026  
  M.S. in Artificial Intelligence, Korea University–KIST Cooperative Graduate Program.

- **Carnegie Mellon University** · 2025–2026  
  Visiting Student, Intensive AI Program sponsored by the Korean government.  
  **Ranked 1st in the 25-participant cohort.**

- **Ewha Womans University** · 2018–2024  
  B.S. in Computer Science and Engineering and Brain & Cognitive Sciences (double major).  
  Graduated **magna cum laude**.

## Selected Honors

- **Presidential Science Scholarship for Graduate Students** · 2024–2026  
  Selected as one of 25 first-year master's students nationwide.  
  [News coverage (Korean)](https://www.asiatime.co.kr/article/20240523500260)

- **Outstanding Graduate Award, KIST** · 2026  
  Selected as one of two master's graduates recognized institute-wide.

## Outside the Lab

<div class="about-personal">
  <div class="about-personal-text">
    <p>
      When I need a break from research, I listen to classical music and songs from musicals.
      I especially love <a href="https://youtu.be/DPJL488cfRw">Yunchan Lim's performance of Rachmaninoff's Piano Concerto No. 3</a>
      and <a href="https://youtu.be/EocLKUzsaoc">"Le temps des cathédrales"</a> from <em>Notre-Dame de Paris</em>.
      Lately, I've also been enjoying Laufey, especially <a href="https://youtu.be/GTIeVJh1Fvo">"Falling Behind"</a>.
    </p>
    <p>Petting Kinyangi (키냥이), a well-known cat at KIST, is another way I unwind.</p>
  </div>
  {% assign campus_cat = site.static_files | where: "path", page.cat_image | first %}
  {% if campus_cat %}
  <figure class="about-cat">
    <img src="{{ page.cat_image | relative_url }}" alt="Kinyangi, a cat at KIST" width="1536" height="865" loading="lazy" decoding="async">
    <figcaption>My best shot of Kinyangi.</figcaption>
  </figure>
  {% endif %}
</div>
