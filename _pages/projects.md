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
      Results across six benchmarks for BioMistral-7B and Llama-3.1-8B-Instruct. Arrows indicate the preferred direction for each metric. The method diagram labels the two response-generating policies π<sub>LT</sub> and π<sub>MT</sub>. The results table uses M<sub>LT</sub> and M<sub>MT</sub> for the corresponding models and M<sub>ASC</sub> for the final model after medical preference training.

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

_KIST · Master's research, 2024-2026_

My master’s research at KIST examined how disinhibitory circuits shape multisensory integration. When auditory and visual signals converge, does disinhibition help downstream neurons distinguish one stimulus combination from another? To address this question, I built two four-layer Hodgkin-Huxley feedforward networks representing primary auditory cortex (A1) and primary visual cortex (V1), both projecting to a shared output layer.

As model inputs, I used spike trains that my collaborators recorded from mouse A1 and V1 while presenting tones and visual gratings together. For each A1-V1 neuron pair, we selected two auditory and two visual stimuli based on the neurons’ responses. This gave four tone-grating combinations, with 10 trials per combination in the input set. In each model pathway, 10% of the input-layer neurons received spike times recorded from the corresponding cortical area. The remaining 90% received simulated spontaneous activity, with firing rates drawn from a log-normal distribution.

Using the same inputs, I compared three circuits: a baseline with no cross-modal connections, a circuit with direct A1-to-V1 excitation, and a circuit incorporating VIP<sup>+</sup>-SST<sup>+</sup> disinhibition. I measured how much information the output population’s firing rate carried about the four stimulus combinations. Direct excitation increased firing but reduced mutual information on average. The disinhibitory circuit had a similar mean mutual information to the baseline, but its effect varied across simulations. Gains tended to be larger when the baseline circuit carried less stimulus information and when auditory activity was stronger relative to visual activity. I am currently preparing a first-author manuscript on this work.

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

_Student-led collaboration initiated in CMU's Introduction to Deep Learning course · 2025-2026_

At Carnegie Mellon University, my collaborators and I asked whether general safety preferences could be used to align a language model for medical questions without collecting new medical preference labels. We developed **Adversarial Self-Correction (ASC)**, a method that starts with two copies of the same language model. We trained both copies on the same general safety dataset using direct preference optimization (DPO). The first model, M<sub>LT</sub> (_less toxic_), learned to favor the response originally marked as preferred. For the second, M<sub>MT</sub> (_more toxic_), we swapped the preferred and rejected responses in every pair. The two models therefore learned opposing preferences from exactly the same examples.

We then gave both models the same medical questions from MedQuAD and collected one answer from each. For each question, we assigned the answer from M<sub>LT</sub> as the preferred response and the answer from M<sub>MT</sub> as the rejected response. This let us build medical preference pairs without asking a clinician or an external model to rank the answers. We then continued training M<sub>LT</sub> on these pairs to obtain the final model, M<sub>ASC</sub>. Comparing M<sub>ASC</sub> with M<sub>LT</sub> shows what the medical training step adds beyond general safety alignment.

We evaluated ASC on BioMistral-7B and Llama-3.1-8B-Instruct across six benchmarks. For BioMistral-7B, the share of unsafe XSTest requests the model complied with fell from 10.5% with M<sub>LT</sub> to 5.0% with M<sub>ASC</sub>. MedQA accuracy held at 43.8%, although the model also answered fewer safe requests (62.4%, down from 66.8%). Results on Llama-3.1-8B-Instruct varied across benchmarks. I led the project beyond the original course and was first author on the resulting paper, accepted at the GenAI4Health workshop at NeurIPS 2026.

{% for figure in page.asc_figures %}
{% assign research_image = site.static_files | where: "path", figure.path | first %}
{% if research_image %}
<figure class="research-figure">
  <a href="{{ figure.path | relative_url }}" target="_blank" rel="noopener noreferrer" aria-label="Open full-size image: {{ figure.label | escape }}" title="Open full-size image">
    <img src="{{ figure.path | relative_url }}" alt="{{ figure.alt | escape }}" width="{{ figure.width }}" height="{{ figure.height }}" loading="lazy" decoding="async">
  </a>
  <figcaption><strong>{{ figure.label | escape }}</strong> {{ figure.caption | escape | replace: '&lt;sub&gt;', '<sub>' | replace: '&lt;/sub&gt;', '</sub>' }}</figcaption>
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
  pp. 324-327, 2026. **Peer-reviewed conference proceedings.**

### Transformer-Based Spiking Neural Networks

I reviewed how researchers combine transformer architectures with spiking neural networks, which represent activity through discrete spikes. I presented this work at the 2025 Conference on Electronics, Semiconductor, and AI, where it received an Outstanding Poster Award.

- **A Review of Transformer-Based Spiking Neural Networks for Brain-Inspired Artificial Intelligence.**  
  Seungyoun Lee, Jae-Ho Han, and Hyun Jae Jang.  
  Conference on Electronics, Semiconductor, and AI, Gangneung, South Korea, 2025. **Poster presentation.**
