# Reading List — Interesting Paper and Blog Post

A living reading list of interesting papers

> **Last updated:** YYYY-MM-DD · **Total papers:** 0 (update as you go)

---

 [A Survival Guide to a PhD](https://karpathy.github.io/2016/09/07/phd/)

  
 [Feynman vs. Computer](https://entropicthoughts.com/feynman-vs-computer)

## unsorted 

[J-Anchor: Defending Against Prefill Attacks via J-Space Selective Refusal Restoration](https://arxiv.org/abs/2611.01342)

## How to use this list

- M = must-read / foundational
- `[ ]` = not read yet, `[x]` = read
- Entry format: **title (link)** — first author, year — one-line takeaway in your own words
- Longer notes go in `notes/<id>.md` (problem, method, results, limitations, relevance to my work)

### Entry template

```markdown
- [ ] [Paper Title](https://arxiv.org/abs/XXXX.XXXXX) — Author et al., YYYY — One-line takeaway. M
```

---

## Table of contents

0.[Links](#Links).
0. [Start here: the J-space paper](#0-start-here-the-j-space-paper)
1. [Jacobian & gradient foundations](#1-jacobian--gradient-foundations)
2. [Reading internal states: lenses & probes](#2-reading-internal-states-lenses--probes)
3. [Causal interventions, steering & feature discovery](#3-causal-interventions-steering--feature-discovery)
4. [Evaluation awareness, deception & hidden goals](#4-evaluation-awareness-deception--hidden-goals)
5. [Chain-of-thought, silent reasoning & monitorability](#5-chain-of-thought-silent-reasoning--monitorability)
6. [Monitoring, control & anomaly detection for safety](#6-monitoring-control--anomaly-detection-for-safety)
7. [Global workspace theory & consciousness background](#7-global-workspace-theory--consciousness-background)
8. [Core AI-safety framing](#8-core-ai-safety-framing)


---


## Links

https://transformer-circuits.pub/2026/workspace/index.html
https://www.lesswrong.com/posts/nv8oedrnLXKRzNEL9/r-lens-making-j-lens-more-faithful-on-early-layers
https://github.com/safety-research/jpp_lens
https://transformer-circuits.pub/2026/october-update/index.html
https://www.neuronpedia.org/qwen3.6-27b/jlens?shareId=cmuyz763o0001182xcprl8ar8


## 0. Start here: the J-space paper





- [ ]  [A global workspace in language models](https://www.anthropic.com/research/global-workspace) — Anthropic, 6 Jul 2026 — Introduces **J-space**, a small internal workspace in Claude found with the **Jacobian lens (J-lens)**; reports causal experiments and safety readouts (evaluation awareness, fabrication, hidden goals).
- [ ]  [From Latent Space to Jacobian Space: Measuring, Evading, and Training Against Safety-Content Accessibility](https://arxiv.org/abs/2610.04316) — Mohammad Mosafer, Oct 2026 — Links latent-space safety directions (representation engineering) to J-space via a layer-wise transport-amplification profile and a paired base-vs-tuned protocol; finds DPO can install refusal while J-space recognition drops to chance, and that monitor-aware suffix attacks evade a prompt-side monitor at no behavioral cost, with only a learned monitor surviving adaptive re-attack. *(Noted from the abstract only.)*
- [ ]  [anthropics/jacobian-lens](https://github.com/anthropics/jacobian-lens) — Official implementation (Apache-2.0, Python). Run it before theorizing about it.
- [ ] [Neuronpedia](https://www.neuronpedia.org) — Interactive J-lens demo for open-weight models (per Anthropic's announcement; check the site for the current demo link).

**Quick mental model** (from secondary coverage — verify against the paper): for each vocabulary word, the J-lens finds the internal activity pattern that makes the model more likely to say that word at some later point; applied to a hidden state, it yields a readable list of "silent words". Known limitation noted in coverage: it only captures concepts that map to a single token.

## 1. Jacobian & gradient foundations

The math behind the lens: how outputs respond to small changes in internal states or inputs.

- [ ] [Intriguing Properties of Neural Networks](https://arxiv.org/abs/1312.6199) — Szegedy et al., 2013 — Adversarial examples; Lipschitz view of network sensitivity. 
- [ ] [Deep Inside Convolutional Networks: Visualising Image Classification Models and Saliency Maps](https://arxiv.org/abs/1312.6034) — Simonyan et al., 2013 — Input-gradient saliency, the earliest "read the Jacobian" interpretability tool.
- [ ] [Explaining and Harnessing Adversarial Examples](https://arxiv.org/abs/1412.6572) — Goodfellow et al., 2014 — Gradient-sign attacks; linearity explanation. 
- [ ] [The Limitations of Deep Learning in Adversarial Settings](https://arxiv.org/abs/1511.07528) — Papernot et al., 2015 — Jacobian-based saliency map attack (JSMA).
- [ ] [Axiomatic Attribution for Deep Networks](https://arxiv.org/abs/1703.01365) — Sundararajan et al., 2017 — Integrated Gradients and attribution axioms.
- [ ] [Parseval Networks](https://arxiv.org/abs/1704.08847) — Cissé et al., 2017 — Controlling the Lipschitz constant / Jacobian norm for robustness.
- [ ] [Spectral Normalization for GANs](https://arxiv.org/abs/1802.05957) — Miyato et al., 2018 — Constraining layer Jacobian spectral norms.
- [ ] [Robust Learning with Jacobian Regularization](https://arxiv.org/abs/1908.02729) — Hoffman et al., 2019 — Penalizing the input-output Jacobian for robustness.
- [ ] [Neural Tangent Kernel](https://arxiv.org/abs/1806.07572) — Jacot et al., 2018 — Parameter-space Jacobian view of training dynamics.
- [ ] [Certified Adversarial Robustness via Randomized Smoothing](https://arxiv.org/abs/1902.02918) — Cohen et al., 2019 — Provable robustness guarantees.

## 2. Reading internal states: lenses & probes

Predecessors and neighbors of the J-lens: decoding what hidden states "mean" without waiting for the output.

- [ ] [Eliciting Latent Predictions from Transformers with the Tuned Lens](https://arxiv.org/abs/2303.08112) — Belrose et al., 2023 — Per-layer learned affine maps improve on the logit lens. 
- [ ] [Future Lens: Anticipating Subsequent Tokens from a Single Hidden State](https://arxiv.org/abs/2311.04897) — Pal et al., 2023 — Hidden states already encode tokens several steps ahead.
- [ ] [Patchscopes: A Unifying Framework for Inspecting Hidden Representations](https://arxiv.org/abs/2401.06102) — Ghandeharioun et al., 2024 — Let the model itself verbalize its hidden states.
- [ ] [Do Llamas Work in English? On the Latent Language of Multilingual Transformers](https://arxiv.org/abs/2402.10588) — Wendler et al., 2024 — Logit-lens evidence for language-independent intermediate concepts.
- [ ] [Discovering Latent Knowledge in Language Models Without Supervision](https://arxiv.org/abs/2212.03827) — Burns et al., 2022 — Unsupervised probing for truth-like directions.
- [ ] [Representation Engineering: A Top-Down Approach to AI Transparency](https://arxiv.org/abs/2310.01405) — Zou et al., 2023 — Reading and controlling population-level representations. 
- [ ] [The Linear Representation Hypothesis and the Geometry of LLMs](https://arxiv.org/abs/2311.03658) — Park et al., 2023 — Formalizing "concepts are directions".

## 3. Causal interventions, steering & feature discovery

J-space claims are *causal* (edit the workspace, change the output). These are the methods and priors for that style of evidence.

- [ ] [Locating and Editing Factual Associations in GPT (ROME)](https://arxiv.org/abs/2202.05262) — Meng et al., 2022 — Causal tracing and targeted edits. 
- [ ] [Steering Language Models With Activation Engineering (ActAdd)](https://arxiv.org/abs/2308.10248) — Turner et al., 2023 — Steering by adding activation differences.
- [ ] [Refusal in Language Models Is Mediated by a Single Direction](https://arxiv.org/abs/2406.11717) — Arditi et al., 2024 — A safety behavior reduced to one direction. 
- [ ] [Toy Models of Superposition](https://arxiv.org/abs/2209.10652) — Elhage et al., 2022 — Why features aren't neuron-aligned.
- [ ] [Sparse Autoencoders Find Highly Interpretable Features in Language Models](https://arxiv.org/abs/2309.08600) — Cunningham et al., 2023 — SAEs for dictionary learning on activations.
- [ ] [Sparse Feature Circuits](https://arxiv.org/abs/2403.19647) — Marks et al., 2024 — Causal graphs over SAE features.
- [ ] [Scaling Monosemanticity](https://transformer-circuits.pub/2024/scaling-monosemanticity/) — Anthropic, 2024 — SAE features in a production-scale model. 
- [ ] [Circuit Tracing: Revealing Computational Graphs in Language Models](https://transformer-circuits.pub/2025/attribution-graphs/methods.html) — Anthropic, 2025 — Attribution-graph methodology.
- [ ] [On the Biology of a Large Language Model](https://transformer-circuits.pub/2025/attribution-graphs/biology.html) — Anthropic, 2025 — Case studies: planning, multi-step reasoning, language-independent concepts. 

## 4. Evaluation awareness, deception & hidden goals

What J-lens readouts are used to catch, and the behavioral work they complement.

- [ ] [Sleeper Agents: Training Deceptive LLMs that Persist Through Safety Training](https://arxiv.org/abs/2401.05566) — Hubinger et al., 2024 
- [ ] [Alignment Faking in Large Language Models](https://arxiv.org/abs/2412.14093) — Greenblatt et al., 2024 
- [ ] [Frontier Models are Capable of In-context Scheming](https://arxiv.org/abs/2412.04984) — Meinke et al., 2024
- [ ] [Large Language Models Often Know When They Are Being Evaluated](https://arxiv.org/abs/2505.23836) — Needham et al., 2025 — Evaluation awareness, measured behaviorally; compare with J-lens readouts.
- [ ] [Agentic Misalignment](https://www.anthropic.com/research/agentic-misalignment) — Anthropic, 2025 — The blackmail-style scenarios referenced in J-space coverage.
- [ ] [Discovering Language Model Behaviors with Model-Written Evaluations](https://arxiv.org/abs/2212.09251) — Perez et al., 2022
- [ ] [Emergent Misalignment](https://arxiv.org/abs/2502.17424) — Betley et al., 2025 — Narrow fine-tuning causing broad misalignment.

## 5. Chain-of-thought, silent reasoning & monitorability

If reasoning happens in a workspace that never reaches the output, how much can the visible chain of thought be trusted?

- [ ] [Language Models Don't Always Say What They Think](https://arxiv.org/abs/2305.04388) — Turpin et al., 2023 — Unfaithful chain-of-thought explanations. 
- [ ] [Measuring Faithfulness in Chain-of-Thought Reasoning](https://arxiv.org/abs/2307.13702) — Lanham et al., 2023
- [ ] [Monitoring Reasoning Models for Misbehavior and the Risks of Promoting Obfuscation](https://arxiv.org/abs/2503.11926) — Baker et al., 2025 — CoT monitoring works, but pressure on CoT can hide intent. 

## 6. Monitoring, control & anomaly detection for safety

Treat internal states as a signal stream: detection, thresholds, and what happens when the monitored system adapts.

- [ ] [AI Control: Improving Safety Despite Intentional Subversion](https://arxiv.org/abs/2312.06942) — Greenblatt et al., 2023 — Monitoring protocols against a model that may be scheming. 
- [ ] [A Baseline for Detecting Misclassified and Out-of-Distribution Examples](https://arxiv.org/abs/1610.02136) — Hendrycks & Gimpel, 2016
- [ ] [A Simple Unified Framework for Detecting OOD Samples and Adversarial Attacks](https://arxiv.org/abs/1807.03888) — Lee et al., 2018 — Mahalanobis distance on internal features.
- [ ] [Deep Anomaly Detection with Outlier Exposure](https://arxiv.org/abs/1812.04606) — Hendrycks et al., 2018
- [ ] [Towards Deep Learning Models Resistant to Adversarial Attacks](https://arxiv.org/abs/1706.06083) — Madry et al., 2017 — Relevant to whether a model can learn to route around a monitor. 

## 7. Global workspace theory & consciousness background

The J-space paper frames its results as *access*, not experience. Background to read the framing critically.

- [ ] [Consciousness in Artificial Intelligence: Insights from the Science of Consciousness](https://arxiv.org/abs/2308.08708) — Butlin et al., 2023 — Indicator properties derived from theories incl. global workspace.
- [ ] Baars, *A Cognitive Theory of Consciousness* (1988) and Dehaene's work on the global neuronal workspace — original theory (book/papers, not arXiv).

## 8. Core AI-safety framing

- [ ] [Concrete Problems in AI Safety](https://arxiv.org/abs/1606.06565) — Amodei et al., 2016 
- [ ] [Risks from Learned Optimization in Advanced Machine Learning Systems](https://arxiv.org/abs/1906.01820) — Hubinger et al., 2019 — Deceptive alignment framing. 
- [ ] [Unsolved Problems in ML Safety](https://arxiv.org/abs/2109.13916) — Hendrycks et al., 2021
- [ ] [The Alignment Problem from a Deep Learning Perspective](https://arxiv.org/abs/2209.00626) — Ngo et al., 2022


## License

Personal reading list, share and reuse freely.
