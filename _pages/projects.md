---
layout: page
title: Research
permalink: /projects/
description: Computational neuroscience and Artificial Intelligence.
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

## Cross-Modal Feedforward Neural Networks with Disinhibitory Motifs

_KIST · Master's research, 2024–2026_

My master’s research at KIST examined how disinhibitory circuits shape multisensory integration. When auditory and visual signals converge, does disinhibition help downstream neurons distinguish one stimulus combination from another?

I built two Hodgkin–Huxley feedforward networks representing primary auditory cortex (A1) and primary visual cortex (V1), with both pathways converging on a shared output layer. As inputs, I used spike trains that my collaborators recorded from mouse A1 and V1 during presentations of tones and visual gratings. Using the same inputs, I compared three circuits. The baseline had no connections between the pathways. The second added direct excitation from A1 to V1. The third also included a disinhibitory circuit in which VIP interneurons inhibited SST interneurons, relieving inhibition of pyramidal neurons.

I measured how much information the output population’s firing rate carried about the stimulus using mutual information. Direct excitation increased firing but reduced stimulus information on average. With disinhibition, stimulus information rose above baseline in 36 of 75 input sets and fell below it in 39. Larger gains tended to occur when auditory activity was stronger relative to visual activity. In the five cases with the largest gains, I also found that the source of excitation to SST neurons mattered. Input from the same V1 layer produced larger gains in visual information than input from A1, while gains in auditory information were similar on average.

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
  _Journal of Computational Neuroscience_, 54(Suppl. 1), Abstract P163, 2026. **Published conference abstract.**

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

## LLM Safety Alignment in the Medical Domain

_Student-led collaboration initiated in CMU's Introduction to Deep Learning course · 2025–2026_

At Carnegie Mellon University, my collaborators and I asked whether general safety preferences could help align a medical language model without collecting new labels for medical responses. We developed Adversarial Self-Correction (ASC), a method that trains two copies of the same model using direct preference optimization (DPO). One learns from the original safety preferences, while the other learns from the same examples with the preferences reversed. We then give both models the same medical prompt and treat the first model’s response as preferred. This gives us a pair of responses for medical safety training without asking an external judge to rank them.

We evaluated ASC on BioMistral-7B and Llama-3.1-8B-Instruct across six benchmarks. Compared with general-safety DPO, ASC reduced the share of unsafe XSTest requests that BioMistral-7B answered from 10.5% to 5.0%, while preserving accuracy on MedQA. The model also answered fewer safe requests, with compliance falling from 66.8% to 62.4%. Results on Llama-3.1-8B-Instruct were mixed. I led the project beyond the original course, and our first-author paper was accepted at the GenAI4Health workshop at NeurIPS 2026.

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

How can we test a biophysical network simulation when the exact output is unknown? In NeuroCERT, I explored how to turn expectations about a simulation’s behavior into tests that can be run on the model.

- **Poster: NeuroCERT: Executable Testing for Oracle-Limited Biophysical Network Simulation.**  
  Seungyoun Lee, Hyun Jae Jang, and Jae-Ho Han.  
  IEEE International Conference on Software Testing, Verification and Validation (ICST),
  pp. 324–327, 2026. **Peer-reviewed conference proceedings.**

### Transformer-Based Spiking Neural Networks

I reviewed how researchers combine transformer architectures with spiking neural networks, which represent activity through discrete spikes. I presented this work at the 2025 Conference on Electronics, Semiconductor, and AI, where it received an Outstanding Poster Award.

- **A Review of Transformer-Based Spiking Neural Networks for Brain-Inspired Artificial Intelligence.**  
  Seungyoun Lee, Jae-Ho Han, and Hyun Jae Jang.  
  Conference on Electronics, Semiconductor, and AI, Gangneung, South Korea, 2025. **Poster presentation.**
  
