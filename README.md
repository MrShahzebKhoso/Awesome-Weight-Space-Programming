# Awesome Weight-Space Programming [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of papers, code, benchmarks, reproductions and discussion on **Weight-Space Programming (WSP)**: language models that read, edit and write the weights of neural networks directly, by reasoning rather than through gradient descent.

<p align="center">
  <img src="https://img.shields.io/badge/papers-20%2B-blue" alt="papers">
  <img src="https://img.shields.io/badge/field%20born-Nov%202026-orange" alt="since">
  <img src="https://img.shields.io/badge/PRs-welcome-brightgreen" alt="PRs welcome">
  <img src="https://img.shields.io/badge/license-CC0-lightgrey" alt="license">
</p>

---

## What is Weight-Space Programming?

The term was introduced by Rikiya Takehi, Jayden Teoh, Alex Zhang and Omar Khattab (MIT CSAIL) on **2 November 2026** in the blog post *Sparks of Weight-Space Programming*. They define it as a setup in which:

> a general-purpose LLM reads and writes a network's weights directly (i.e., not through an optimizer, and in particular not with gradient descent).

The working idea is that **weights are a program**. A model looks at raw parameters, works out what each part computes or should compute, and changes the numbers on purpose, the way an engineer edits source code.

```
        ┌──────────────────────┐   natural-language goal
        │   "Editor" LLM       │◀── "stop this model looping",
        │  (GPT-6 Astra, Qwen, │    "write a Breakout policy"
        │   Claude, Kimi, …)   │
        └─────────┬────────────┘
     read │       │ write / edit (no optimizer)
          ▼       ▼
        ┌──────────────────────┐
        │   Target network θ   │  game policy · CNN · ViT · LLM · diffusion U-Net
        └──────────────────────┘
```

WSP sits where three older fields meet: **weight-space learning** (networks as a data modality), **mechanistic interpretability** (understanding what weights compute) and **model editing** (targeted changes to parameters). See [Foundations & Related Fields](#foundations--related-fields).

---

## Contents

- [The Origin](#the-origin)
- [Papers](#papers)
  - [Capabilities & Critical Analysis](#capabilities--critical-analysis)
  - [Benchmarks](#benchmarks)
  - [Writing Networks from Scratch](#writing-networks-from-scratch)
  - [Editing & Improving Language Models](#editing--improving-language-models)
  - [Vision & Diffusion Models](#vision--diffusion-models)
  - [Science & Domain Applications](#science--domain-applications)
  - [Verification & Interpretability](#verification--interpretability)
- [Code, Models & Demos](#code-models--demos)
- [Reproductions & Critiques](#reproductions--critiques)
- [Explainers & Press](#explainers--press)
- [Foundations & Related Fields](#foundations--related-fields)
- [Open Problems](#open-problems)
- [Contributing](#contributing)

---

## The Origin

- **Sparks of Weight-Space Programming: LLMs can natively read & write neural network weights**: Takehi, Teoh, Zhang, Khattab (MIT CSAIL), Nov 2026. [[blog]](https://rikiyat.github.io/blog/weight-space-programming/) [[logs]](https://github.com/RikiyaT/lm_understand-logs)
  - **Read:** from 17,253 raw weights and no tools, GPT-6 Astra identified a game-playing policy as Breakout.
  - **Fix:** a single edit to about 3.5% of a PPO policy's weights raised its success on a car level from 0% to 100%.
  - **Improve:** an edit to 0.016% of Qwen3.5-0.8B's weights, which suppressed a thinking-loop direction, raised MATH-500 from 7.9% to 48.1%.
  - **Write:** networks written from scratch, with no environment feedback, that the authors report outplay PPO policies trained for 100M steps.
  - **Failures:** sycophancy in a language model could not be detected from the weights alone.

---

## Papers

> All entries are arXiv preprints from November 2026 unless noted. Listed newest-first within each section.

### Capabilities & Critical Analysis

- **Exploring Weight-Space Programming: Capabilities, Generalization, and Limitations**. [[arXiv 2611.09382]](https://arxiv.org/abs/2611.09382)
  Edits learned on math transfer to GPQA Diamond, IFEval and SciBench. Results vary widely across trajectories, and 6 of 16 runs keep the original weights because no candidate edit could be validated.
- **Can an LLM Actually Reason and Program about Neural Network's Weights or is it just memorization on steroids?** Nazmus Sakib Ahmed. [[arXiv 2611.08070]](https://arxiv.org/abs/2611.08070)
  Finds zero-shot weight reading is better described as "local arithmetic plus priors" than as tracing how weights compute.
- **Compiling Known Rules into Compact Neural Agents: Weight-Space Programming on Unseen Games**. Jens Lehmann. [[arXiv 2611.16981]](https://arxiv.org/abs/2611.16981)
  WSP networks turn out to be "programs in network form": 93% of parameters are exactly zero. Plain Python programs written by the same LLMs beat the networks they write.

### Benchmarks

- **WeightBench: Evaluating Language Models as Weight-Space Programmers**. [[arXiv 2611.18553]](https://arxiv.org/abs/2611.18553)
  Benchmark of 42 tasks in five tracks: reading, fixing, writing, spotting impossible edits, and data-free compression. Targets range from 2K-parameter policies to 7B-parameter LLMs, with budgeted agent access.
- **Training Vision Models for LLM-Driven Weight-Space Programming**. [[arXiv 2611.26408]](https://arxiv.org/abs/2611.26408)
  A vision WSP benchmark in which five LLMs edit CNNs and ViTs on Waterbirds, CIFAR-100, PACS and Entity-30. It releases more than 75,000 logged tool calls.
- **Zero-Shot Weight-Space Programming Across a Difficulty-Graded Ladder of Two-Player Games**. [[arXiv 2611.09271]](https://arxiv.org/abs/2611.09271)
  Gives a formal definition of a "weight-space programmed" network and builds a ladder of ten networks from reusable gate primitives.

### Writing Networks from Scratch

- **Physics2Weight: Direct Neural Network Architecture and Weight Generation from Physical Laws Using LLMs**. [[arXiv 2611.12954]](https://arxiv.org/abs/2611.12954)
  The LLM generates both the architecture and the weights from physical laws, then refines them using forward-pass feedback.
- **Weight-Space Programming of Policies and Their Verification via Model Checking**. [[arXiv 2611.11604]](https://arxiv.org/abs/2611.11604)
  Programmed policies hit the optimal probability in all 18 runs and are checked with the Storm model checker, including PCTL safety specs.

### Editing & Improving Language Models

- **Writing Weights or Training Them? Spatial Reasoning through Weight-Space Programming and Low-Rank Adaptation**. Yalin Yang et al. [[arXiv 2611.27089]](https://arxiv.org/abs/2611.27089)
  Compares WSP head-to-head with LoRA fine-tuning.
- **Weight-Space Programming Writes In-Context Learning and Matches Fine-Tuning in Language Models**. Konstantinos Skianis, Aristidis Likas. [[arXiv 2611.26841]](https://arxiv.org/abs/2611.26841)
  Turns in-context examples into a weight update for a weaker LM.
- **WeightCode: Installing New Capabilities into Neural Networks via Weight-Space Programming**. Bo Li et al. [[arXiv 2611.25476]](https://arxiv.org/abs/2611.25476)
  A frozen LLM writes executable "weight programs" that add new computations to trained networks. On ImageNet these give net gains of 8.84 to 17.62 points.

### Vision & Diffusion Models

- **Perceptual Weight Space Programming for Diffusion Super-Resolution**. [[arXiv 2611.18690]](https://arxiv.org/abs/2611.18690)
  Edits under 0.1% of the U-Net parameters, spread over at most three layers, of ResShift, SinSR and SUPIR. Compares GPT-6 Astra with Qwen3-VL.
- **WSP for Improving Image-Restoration Diffusion Models: Technical Conjectures and a Recursive Improvement Loop**. Zhuoran Zheng, Doubao. [[arXiv 2611.04268]](https://arxiv.org/abs/2611.04268)
  A conjecture paper that proposes a benchmark for applying WSP to deblurring, super-resolution, denoising and inpainting.

### Science & Domain Applications

- **Weight-space programming and mechanistic interpretability for model editing in particle physics**. Bonnet-Guerrini, Ioannou-Nikolaides, Petersen. [[arXiv 2611.27079]](https://arxiv.org/abs/2611.27079)
  Uses WSP together with SAE-guided edits to remove unwanted behaviour from a particle-physics foundation model.
- **Mixed Signals: Weight-Space Programming for EEG and ECG**. Varam, Aminosharieh Najafi, Atienza (EPFL). [[arXiv 2611.13758]](https://arxiv.org/abs/2611.13758) [[site]](https://daravaram.github.io/BioWSP)
  Finds and fixes planted faults in biosignal models. Networks written from scratch beat classic hand-crafted EEG pipelines.
- **WeightLoop: Weight-Space Programming with Experimental Feedback**. Mengran Li et al. [[arXiv 2611.07319]](https://arxiv.org/abs/2611.07319)
  A reusable WSP editor that turns lab measurements into lasting updates to scientific predictors.

### Verification & Interpretability

- **Interpretable weight-space programming builds transparent transformers and brain encoding models**. [[arXiv 2611.18114]](https://arxiv.org/abs/2611.18114)
  Introduces iWSP, in which an agent builds interpretable models by programming their weights and features in code.
- See also *Policies + Model Checking* [(2611.11604)](https://arxiv.org/abs/2611.11604) and *Particle physics* [(2611.27079)](https://arxiv.org/abs/2611.27079) above.

---

## Code, Models & Demos

| Resource | What it is |
|---|---|
| [RikiyaT/lm_understand-logs](https://github.com/RikiyaT/lm_understand-logs) | Prompts, responses, code and evaluations from the original *Sparks* post |
| [RikiyaT/Qwen3.5-0.8B-weight-space-programming](https://huggingface.co/RikiyaT/Qwen3.5-0.8B-weight-space-programming) | Rebuilt Qwen3.5-0.8B checkpoint carrying the Astra edit |
| [akhaliq/weight-space-programming-demo](https://huggingface.co/spaces/akhaliq/weight-space-programming-demo) | Hugging Face Space for comparing the base and edited models |
| [BioWSP](https://daravaram.github.io/BioWSP) | Project page for WSP on EEG/ECG models |

---

## Reproductions & Critiques

Independent checks of the claims belong in this section.

- **Qwen 3.8 27B on my laptop can interpret model weights, too**: Simon Willison, 3 Nov 2026. [[post]](https://simonwillison.net/2026/Nov/3/qwen-can-interpret-model-weights/)
  Reruns the no-tools reading task with a local quantized model, which named 3 of the 4 games after 45 to 65 minutes of reasoning each. Willison argues a patient human with pencil and paper could probably do the same.
- **The "Astra can read and write weights to improve Qwen" post is massively misleading**: Matthew Honnibal, 3 Nov 2026. [[post]](https://honnibal.dev/blog/astra-read-write-misleading)
  Points out that only the small networks (17K to 172K weights) were edited from raw weights alone. The Qwen result used Python and up to 50 passes over practice problems.
- *Is the Qwen result a capability or a bug fix?* Several write-ups note that the edit removes a thinking-loop direction, so it repairs a known failure rather than adding math ability. Runs with 10 or 25 passes barely moved MATH-500.

---

## Explainers & Press

- [DataCamp: Weight-Space Programming: How LLMs Read and Edit Neural Network Weights](https://www.datacamp.com/blog/weight-space-programming)
- [Snowflake: Fixing a neural network by having an LLM edit its weights](https://www.snowflake.com/en/developers/blog/editing-neural-network-weights-with-an-llm/)
- [The Register: Forget retraining, AI can now tweak another AI's weights](https://www.theregister.com/a/5307105)
- [AI Wiki: Weight-Space Programming](https://aiwiki.ai/wiki/weight_space_programming)
- [Envisioning: Weight-Space Programming (vocabulary)](https://envisioning.com/vocab/weight-space-programming)

---

## Foundations & Related Fields

WSP builds on several older ideas. The papers below are good background reading.

**Weight-space learning (networks as data)**
- **A Survey of Weight Space Learning: Understanding, Representation, and Generation**: Han, Wang et al., 2026. [[arXiv 2603.10090]](https://arxiv.org/abs/2603.10090)
- **Equivariant Architectures for Learning in Deep Weight Spaces (DWSNets)**: Navon et al., ICML 2023. [[arXiv 2301.12780]](https://arxiv.org/abs/2301.12780) [[code]](https://github.com/AvivNavon/DWSNets)
- **Permutation Equivariant Neural Functionals**: Zhou et al., NeurIPS 2023. [[arXiv 2302.14040]](https://arxiv.org/abs/2302.14040)
- **Learning to Learn with Generative Models of Neural Network Checkpoints (G.pt)**: Peebles et al., 2022. [[arXiv 2209.12892]](https://arxiv.org/abs/2209.12892)
- **HyperNetworks**: Ha, Dai, Le, 2016. [[arXiv 1609.09106]](https://arxiv.org/abs/1609.09106)
- **End-to-End Synthesis of Neural Programs in Weight Space**: Li, Xu, Khalil, Sanner, ICLR 2025. [[page]](https://iclr.cc/virtual/2025/33060)
- ICLR 2025 Workshop on Weight Space Learning. [[site]](https://weight-space-learning.github.io/)

**Hand-written / compiled networks**
- **Thinking Like Transformers (RASP)**: Weiss, Goldberg, Yahav, ICML 2021. [[arXiv 2106.06981]](https://arxiv.org/abs/2106.06981)
- **Tracr: Compiled Transformers as a Laboratory for Interpretability**: Lindner et al., 2023. [[arXiv 2301.05062]](https://arxiv.org/abs/2301.05062)
- **Linear Transformers Are Secretly Fast Weight Programmers**: Schlag, Irie, Schmidhuber, ICML 2021. [[arXiv 2102.11174]](https://arxiv.org/abs/2102.11174)
- **Software 2.0**: Andrej Karpathy, 2017. [[essay]](https://karpathy.medium.com/software-2-0-a64152b37c35)

**Direct weight editing**
- **Locating and Editing Factual Associations in GPT (ROME)**: Meng et al., NeurIPS 2022. [[arXiv 2202.05262]](https://arxiv.org/abs/2202.05262)
- **Editing Models with Task Arithmetic**: Ilharco et al., ICLR 2023. [[arXiv 2212.04089]](https://arxiv.org/abs/2212.04089)
- **Refusal in Language Models Is Mediated by a Single Direction**: Arditi et al., 2024. [[arXiv 2406.11717]](https://arxiv.org/abs/2406.11717)

**Other awesome lists**
- [Zehong-Wang/Awesome-Weight-Space-Learning](https://github.com/Zehong-Wang/Awesome-Weight-Space-Learning)
- [ege-erdogan/awesome-weight-space-learning](https://github.com/ege-erdogan/awesome-weight-space-learning)

---

## Open Problems

The questions below come up repeatedly across the papers and critiques. Each could anchor a project.

1. **Reading vs. search.** When an edit improves a benchmark, did the LLM *understand* the weights, or did it find the edit by trial and error with feedback? How to report budgets (passes, tool calls, tokens) in a comparable way is still an open question.
2. **Scale.** Edits made from raw weights alone have only been shown on networks with tens of thousands of parameters. LLM-scale results so far depend on code, activations and evaluation loops.
3. **Repair vs. capability.** Many successes fix one localized fault. Can WSP *add* knowledge or skills that are spread across many weights?
4. **Distributed behaviours.** Properties such as sycophancy did not show up in the weights alone. What should the editor be shown to detect them (activations, attention, SAE features)?
5. **Verification.** Model checking, interpretable-by-construction edits and held-out evaluation are early approaches to trusting a written network.
6. **Safety.** LLMs that can edit weights, possibly including their own, raise new questions about oversight and tamper detection.

---

## Contributing

Contributions are very welcome. The field is only weeks old and new preprints appear every few days. Please read [CONTRIBUTING.md](CONTRIBUTING.md) before opening a pull request.

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, the contributors have waived all copyright and related rights to this work.
