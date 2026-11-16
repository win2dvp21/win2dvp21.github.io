---
layout: page
title: Research
permalink: /projects/
description: Computational neuroscience and language-model safety.
nav: true
nav_order: 1

# Upload all three images to assets/img/research/.

multisensory_figures:
  - path: /assets/img/research/multisensory-model.png
    width: 2048
    height: 767
    label: "Multisensory simulation and analysis."
    alt: "Recorded and spontaneous spike inputs drive parallel four-layer auditory and visual networks that converge on a shared output, followed by firing-rate and mutual-information analysis."
    caption: >-
      Recorded A1 and V1 spike patterns and spontaneous activity drive two four-layer feedforward pathways that converge on a shared output. Output responses are analyzed using firing rates and mutual information.

asc_figures:
  - path: /assets/img/research/asc-method.png
    width: 2400
    height: 1067
    label: "ASC method."
    alt: "Original and reversed general-safety preferences train two policies whose medical responses form chosen and rejected pairs for domain-specific DPO."
    caption: >-
      Two sibling policies are trained using original and reversed general-safety preferences. For each medical prompt, the aligned policy's response is assigned as chosen and the inverted policy's response as rejected. These pairs are used for domain-specific DPO without new medical preference annotations or an external judge.
  - path: /assets/img/research/asc-results.png
    width: 1822
    height: 840
    label: "Evaluation results."
    alt: "Benchmark results for BioMistral-7B and Llama-3.1-8B-Instruct, comparing the initial model, general-safety DPO, supervised fine-tuning, ASC, and the inverted policy."
    caption: >-
      Results across six benchmarks for BioMistral-7B and Llama-3.1-8B-Instruct. Arrows indicate the preferred direction for each metric. M_LT is the general-safety DPO baseline, M_ASC is ASC, and M_MT is the inverted policy shown for diagnosis.

_styles: |
  .research-figure {
    margin: 1.5rem 0 2rem;
  }
  .research-figure > a {
    display: block;
    background: #fff;
    border-radius: 4px;
    overflow: hidden;
    cursor: zoom-in;
  }
  .research-figure img {
    display: block;
    width: 100%;
    max-width: 100%;
    height: auto;
    background: #fff;
  }
  .research-figure figcaption {
    margin-top: 0.6rem;
    font-size: 0.9rem;
    line-height: 1.5;
  }
---

## Disinhibition & Multisensory Integration

_KIST · Master's research, 2024–2026_

My master's research examined how disinhibitory circuits affect information
transmission when auditory and visual inputs converge. I built biophysical
feedforward networks of auditory and visual cortical neurons and compared three
configurations: no cross-modal connections, direct excitation, and excitation
plus disinhibition. I drove the networks with spikes recorded from mouse primary
auditory (A1) and visual (V1) cortex and analyzed the information carried by the output.

Direct excitation increased output firing but reduced mutual information on
average. Disinhibition produced gains for some input conditions and losses for
others, with mean mutual information comparable to baseline. I also varied the
source of excitation to SST interneurons to examine its effects on auditory and
visual information transmission.

{% for figure in page.multisensory_figures %}
{% assign research_image = site.static_files | where: "path", figure.path | first %}
{% if research_image %}
<figure class="research-figure">
  <a href="{{ figure.path | relative_url }}" target="_blank" rel="noopener noreferrer" aria-label="Open full-size image: {{ figure.label | escape }}" title="Open full-size image">
    <img src="{{ figure.path | relative_url }}" alt="{{ figure.alt | escape }}" width="{{ figure.width }}" height="{{ figure.height }}" loading="lazy" decoding="async">
  </a>
  <figcaption><strong>{{ figure.label | escape }}</strong> {{ figure.caption | escape }}</figcaption>
</figure>
{% endif %}
{% endfor %}

### Related Publications & Presentations

- **Distinct disinhibitory circuits differentially modulate the multisensory integration in a feedforward network.**  
  Seung-Youn Lee, Kyujin Kang, Yebeen Yoon, Jae-Ho Han, and Hyun Jae Jang.  
  *Journal of Computational Neuroscience*, 54(Suppl. 1), Abstract P163, 2026. **Published conference abstract.**

- **Disinhibition of Distinct Inhibitory Circuits Differentially Modulates Multisensory Integration of In Vivo Spike Patterns in a Cross-Modal Feedforward Network.**  
  Seungyoun Lee, Kyujin Kang, Yebeen Yoon, Jae-Ho Han, and Hyun Jae Jang.  
  Korean Society for Computational Neuroscience (CBrain), Seoul, South Korea, 2025. **Poster presentation.**

- **Disinhibitory Circuits Enhance Information Integration in Converging Feedforward Networks of Cortical Columns.**  
  Seungyoun Lee, Jae-Ho Han, and Hyun Jae Jang.  
  Society for Neuroscience (SfN), Chicago, IL, USA, 2024. **Poster presentation.**

- **Enhanced Information Integration by Disinhibitory Circuit in a Feedforward Network Model.**  
  Seungyoun Lee, Jae-Ho Han, and Hyun Jae Jang.  
  Korean Society for Brain and Neural Sciences (KSBNS), Gyeongju, South Korea, 2024. **Poster presentation.**

---

<br />

## Medical LLM Safety Alignment

_Student-led collaboration initiated in CMU's Introduction to Deep Learning course · 2025–2026_

I developed Adversarial Self-Correction (ASC) to construct medical preference
data without new domain annotations or external judges. Using direct preference
optimization (DPO), I trained two sibling policies on original and reversed
general-safety preferences. Their responses to medical prompts formed new
preference pairs, with the aligned policy's response treated as preferred.

I evaluated ASC on BioMistral-7B and Llama-3.1-8B-Instruct across six benchmarks
covering safety, over-refusal, and utility. Compared with the general-safety DPO
baseline, ASC reduced BioMistral-7B's unsafe-request compliance on XSTest from
10.5% to 5.0% while preserving MedQA accuracy. Safe-prompt compliance decreased
from 66.8% to 62.4%, and results on Llama-3.1-8B-Instruct were mixed.
I led the project's continuation beyond the course, resulting in a first-author
paper accepted at GenAI4Health, a NeurIPS 2026 workshop.

{% for figure in page.asc_figures %}
{% assign research_image = site.static_files | where: "path", figure.path | first %}
{% if research_image %}
<figure class="research-figure">
  <a href="{{ figure.path | relative_url }}" target="_blank" rel="noopener noreferrer" aria-label="Open full-size image: {{ figure.label | escape }}" title="Open full-size image">
    <img src="{{ figure.path | relative_url }}" alt="{{ figure.alt | escape }}" width="{{ figure.width }}" height="{{ figure.height }}" loading="lazy" decoding="async">
  </a>
  <figcaption><strong>{{ figure.label | escape }}</strong> {{ figure.caption | escape }}</figcaption>
</figure>
{% endif %}
{% endfor %}

### Related Publication

- **Break It to Align It: Domain Annotation-Free Medical Safety Alignment via Preference Inversion.**  
  Seungyoun Lee and Seohyun Lee.  
  The Third Workshop on GenAI for Health: Agentic Systems, Clinical Trust, and Future Potential
  (GenAI4Health @ NeurIPS 2026). **Accepted workshop paper.**

---

<br />

## Other Research Activities

<br />

### NeuroCERT: Testing Biophysical Network Simulations

- **Poster: NeuroCERT: Executable Testing for Oracle-Limited Biophysical Network Simulation.**  
  Seungyoun Lee, Hyun Jae Jang, and Jae-Ho Han.  
  IEEE International Conference on Software Testing, Verification and Validation (ICST),
  pp. 324–327, 2026. **Peer-reviewed conference proceedings.**

### Transformer-Based Spiking Neural Networks

- **A Review of Transformer-Based Spiking Neural Networks for Brain-Inspired Artificial Intelligence.**  
  Seungyoun Lee, Jae-Ho Han, and Hyun Jae Jang.  
  Conference on Electronics, Semiconductor, and AI, Gangneung, South Korea, 2025. **Poster presentation.**

