<!--
Ready-to-paste README for https://github.com/MrShahzebKhoso/Awesome-Weight-Space-Programming
Updated 25 Nov 2026. All paper, code, and blog links were taken from the papers themselves
or the founding essay, and the blog/community links were opened and checked on 25 Nov 2026.
-->


# Awesome Weight-Space Programming (WSP)

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
![Research Collection](https://img.shields.io/badge/collection-research-blue)
![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen)
![Last Updated](https://img.shields.io/badge/updated-November%202026-orange)

**A curated research hub for Weight-Space Programming (WSP): research papers, implementations, benchmarks, reproducibility studies, technical discussions, and emerging applications.**

Weight-Space Programming explores how general-purpose Large Language Models (LLMs) can directly **read, write, and edit neural network weights** using natural-language specifications and programmatic tools, without conventional gradient-based training.

This repository tracks the rapidly emerging WSP research ecosystem, from its introduction at MIT CSAIL to new approaches in neural network synthesis, model editing, capability installation, interpretability, verification, and scientific applications.

Whether you are an **AI researcher, machine learning engineer, developer, graduate student, or someone exploring LLM-based neural network programming**, this collection is intended to help you discover relevant research and reproduce experiments.

## Start Here

- 📖 [Foundational Work: Sparks of Weight-Space Programming](#foundational-work)
- 📚 [Research Papers and Surveys](#surveys)
- 🧪 [Benchmarks and Evaluations](#benchmarks--evaluation)
- 💻 [Open-Source Implementations](#replications--reproductions)
- 🧠 [Technical Approaches and Applications](#reading--auditing-weights)
- 🔬 [Related Research and Foundations](#background-related-lines-of-work)
- 🤝 [Contribute Research or Implementations](#contributing)

## What is Weight-Space Programming?

Weight-Space Programming (WSP) is an emerging paradigm introduced by Rikiya Takehi, Jayden Teoh, Alex Zhang, and Omar Khattab at MIT CSAIL in November 2026.

It investigates whether LLMs can operate directly on neural network parameters as programmable objects.

The three core operations are:

- **Read:** Interpret existing neural network weights and infer their learned behavior.
- **Write:** Construct neural network weights from scratch based on a specification.
- **Edit:** Modify existing weights to change, repair, or extend model behavior.

Unlike conventional neural network training, WSP explores gradient-free, LLM-directed parameter construction and modification.

This collection distinguishes direct WSP research from related historical approaches such as hypernetworks, model merging, fast-weight programming, and conventional model editing.

---


## Contents
- [Surveys](#surveys)
- [Foundational Work](#foundational-work)
- [Benchmarks & Evaluation](#benchmarks--evaluation)
- [Reading & Auditing Weights](#reading--auditing-weights)
- [Writing Weights from Scratch](#writing-weights-from-scratch)
- [Editing, Repair & Capability Installation](#editing-repair--capability-installation)
- [Systems, Runtimes & Verification](#systems-runtimes--verification)
- [Critical Perspectives](#critical-perspectives)
- [Replications & Reproductions](#replications--reproductions)
- [Community Extensions (Blogs & Code)](#community-extensions-blogs--code)
- [Commentary & Critiques](#commentary--critiques)
- [Background: Related Lines of Work](#background-related-lines-of-work)
- [Summary Table](#summary-table)
- [Contributing](#contributing)

---

## Surveys
- **Weight-Space Programming: An Early Review of an Emerging Paradigm for Gradient-Free Neural Network Synthesis, Editing, and Auditing**: *Shahzeb Khoso (NUST)*, Nov 2026. A scoping review of the first 15 arXiv studies, covering a read/write/edit taxonomy, a quality appraisal, cross-cutting findings, and open problems. *(Preprint link coming soon.)*

## Foundational Work
- **[Sparks of Weight-Space Programming: LLMs can natively read & write neural network weights](https://rikiyat.github.io/blog/weight-space-programming/)**: *Rikiya Takehi, Jayden Teoh, Alex Zhang, Omar Khattab (MIT CSAIL)*, 2 Nov 2026. The essay that named the field. GPT-6 Astra reads, edits, and writes weights. Editing could unmask a hidden ability but not add a missing one. A "Response to Comments" section was added on 12 Nov. [[💻 logs](https://github.com/RikiyaT/lm_understand-logs)] [[🤗 edited model](https://huggingface.co/RikiyaT/Qwen3.5-0.8B-weight-space-programming)] [[demo](https://huggingface.co/spaces/akhaliq/weight-space-programming-demo)]

## Benchmarks & Evaluation
- **[WeightBench: Evaluating Language Models as Weight-Space Programmers](https://arxiv.org/abs/2611.18553)**: *Aayush Marasini, Barsat Khadka, Nick Rahimi (U. Southern Mississippi)*. 42 tasks in 5 tracks (read, fix, write, impossible-edit recognition, data-free compression) on networks of 2K–7B parameters. Agents run in an OS-level sandbox with a metered NumPy and a hash-chained ledger. Claude Opus 5.5 reaches a macro score of 0.535. [[💻 code](https://github.com/Aayush-Marasini/WeightBench)]
- **[IWIBench: Evaluating Gradient-Free Model Driven Intra-weight Injection](https://arxiv.org/abs/2611.08647)**: *Chris von Csefalvay, Pranav Doma, Achyuthan Unni Krishnan, Tamás Földi*, 5 Nov 2026. Measures how well LLM "editors" modify the weights of a smaller target model (typically Gemma 3 4B IT) to meet ten text-editing objectives.
- **[Exploring Weight-Space Programming: Capabilities, Generalization, and Limitations](https://arxiv.org/abs/2611.09382)**: *Junru Hu et al. (Shanghai AI Laboratory, Tongji, Fudan)*. 16 editing trajectories over 7 benchmarks on Qwen3.5-0.8B and 9B. On the 0.8B model, gains reach +36.7 points, and a 1,023-parameter edit gives +29.5 on MATH-500. The 9B model gains little, and 6 of 16 trajectories keep the original weights. [[🌐 homepage](https://wsp-scope.github.io/)] [[💻 code](https://github.com/WSP-Scope/WSP-Scope-Project)]

## Open-Source Implementations and Tools

A collection of codebases, experimental implementations, and tools
for reproducing and extending Weight-Space Programming research.

| Project | Description | Framework / Tools |
|---|---|---|
| [WeightBench](https://github.com/Aayush-Marasini/WeightBench) | WSP evaluation benchmark | Python |
| [WeightCode](https://github.com/Gen-Verse/WeightCode) | Reusable weight-program installation | See repository |
| [WeightLoop](https://github.com/limengran98/WeightLoop) | Experimental-feedback-driven weight editing | See repository |
| [WSP-Scope](https://github.com/WSP-Scope/WSP-Scope-Project) | WSP experiments and evaluations | See repository |
| [Quantum WSP](https://github.com/DebarshiKunduPSU/Quantum-Weight-Space-Programming) | Weight programming for quantum circuits | See repository |

## Reading & Auditing Weights
- **[Weight-Space Programming for Auditing Clinical Decision Networks](https://arxiv.org/abs/2611.05341)**: *Humza Nusrat, Omar Nusrat (Henry Ford Health, Michigan State, Toronto Metropolitan)*. Claude Opus 5.5 audits radiotherapy decision networks (433–4,801 parameters) blind. It names the broken rule in 16 of 18 flawed networks and repairs each by a median of 3 parameters, but it cannot certify that a network is correct. [[💻 code](https://github.com/hnusrat1/weightspace-rt)]

## Writing Weights from Scratch
- **[Weight-Space Programming for Medical Imaging: Do We Still Need Training Data?](https://arxiv.org/abs/2611.12066)**: *Maximilian Lindholz et al. (Charité – Universitätsmedizin Berlin, BIH, et al.)*. LLMs write LeNet-style CNN weights without seeing any images. They are above chance on all six MedMNIST tasks (mean AUC 0.72), but Adam trained on 256 labels still wins (0.83). [[💻 code](https://github.com/MaximilianLindholz/weight-space-programming-medical)]
- **[Weight-Space Programming for Materials Science](https://arxiv.org/abs/2611.22013)**: *Sk Md Ahnaf Akif Alvi, Raymundo Arróyave (Texas A&M)*. LLM-written networks rank candidates with zero labels (alloys ρ = 0.64–0.79) and serve as Gaussian-process prior means. They help most in the first tens of labels. [[💻 code](https://github.com/sheikhahnaf/weightspace-programming-for-material-science)]
- **[Mixed Signals: Weight-Space Programming for EEG and ECG](https://arxiv.org/abs/2611.13758)**: *Dara Varam, Taraneh Aminosharieh Najafi, David Atienza (EPFL ESL)*. Written biosignal networks match gradient descent with 6× fewer training subjects. The LLMs cannot improve already well-trained networks. [[🌐 project](https://daravaram.github.io/BioWSP)]
- **[Weight-Space Programming of Variational Quantum Circuits](https://arxiv.org/abs/2611.11537)**: *Debarshi Kundu, Swaroop Ghosh, Vasant Honavar (Penn State)*. The LLM writes circuit angles without an optimizer: 95–100% of the VQE spectrum and the exact H₂ ground state in closed form. Accuracy falls to chance once a circuit passes 30 opaque weights. [[💻 code](https://github.com/DebarshiKunduPSU/Quantum-Weight-Space-Programming)]
- **[Weight-Space Programming of Policies and Their Verification via Model Checking](https://arxiv.org/abs/2611.11604)**: *Dennis Gross (artigo.ai)*. DeepSeek-V4-Pro and Kimi-K3.1-Pro write RL policy weights, which are verified against PCTL requirements with Storm/COOL-MC. All 18 created policies reach the optimal probability. [[💻 code](https://github.com/LAVA-LAB/COOL-MC/tree/wsp_verified)]
- **[Weight-Space Programming Doesn't Need Transformers](https://arxiv.org/abs/2611.22055)**: *Hyunjong Ok, Jaeho Lee (POSTECH)*. Free to design their own models, LLMs write sparse associative tables, reaching up to 54.4% on ARC with about 1,800× fewer parameters than their best written Transformer. [[🌐 project](https://wsp-no-transformer.github.io)] [[💻 code](https://github.com/effl-lab/Weight-Space-Programming)]
- **[Interpretable weight-space programming builds transparent transformers and brain encoding models](https://arxiv.org/abs/2611.18114)**: *Yash Mehta, Chandan Singh, Weijia Xu, Richard J. Antonello, Adeen Flinker, Nima Mesgarani, Michael F. Bonner, Nebojsa Jojic, Jianfeng Gao*, 13 Nov 2026. An LLM agent builds interpretable models (transformers and brain encoding models) by writing their weights and features in code, without backpropagation. [[💻 code](https://github.com/csinva/weight-space-programming-autoresearch)] [[📝 report](https://csinva.io/weight-space-programming-autoresearch/analyze/toy_examples/report.html)]

## Editing, Repair & Capability Installation
- **[WeightCode: Installing New Capabilities into Neural Networks via Weight-Space Programming](https://arxiv.org/abs/2611.25476)**: *Bo Li et al. (U. Macau, NUS, CUHK, Oxford, Stanford, Peking, …)*. A frozen LLM writes executable "weight programs" that install new computations. Rerun on 5 independently trained ViTs with no further LLM calls, the programs keep 83–110% of their gains. [[💻 code](https://github.com/Gen-Verse/WeightCode)]
- **[WeightLoop: Weight-Space Programming with Experimental Feedback](https://arxiv.org/abs/2611.07319)**: *Mengran Li et al. (HKISI, U. Macau, UBC, Westlake, …)*. Turns experimental measurements into persistent, validated weight edits, cutting error on scientific predictors by 5.1–18.6%. [[💻 code](https://github.com/limengran98/WeightLoop)]
- **[Can Weight-Space Programming Alter Learned Ethical Priorities?](https://arxiv.org/abs/2611.24330)**: *Kai Yi Ji*. A weight edit shifts how concept-supervised text readers trade honouring a pledge against benefiting more people. Exploratory work with an alignment angle. 

## Systems, Runtimes & Verification
- **[W-ISA: Transactional Execution of Weight-Space Intervention Programs](https://arxiv.org/abs/2611.13232)**: *Ekrem Aksoy*. A shape-checked instruction set and transactional runtime that applies, measures, and rolls back weight interventions. Its edits match PyTorch hooks to within 1.84×10⁻⁴ logit difference.

## Critical Perspectives
- **[Can an LLM Actually Reason and Program about Neural Network's Weights or is it just Memorization on Steroids?](https://arxiv.org/abs/2611.08070)** ⚠️: *Nazmus Sakib Ahmed (BRAC University)*. Argues that zero-shot weight *reading* is "local arithmetic plus dataset priors", not weight-flow tracing. Proposes a label-permutation and forward-pass auditing protocol. [[📝 blog version](https://sakibbai.com/posts/2026-11-05-llm-weight-space-programming/)]
- **[Weight-Space Programming for Vision–Language Model Repair](https://arxiv.org/abs/2611.23615)** ⚠️: *Avinash Goutham Aluguvelly (UT Austin)*. Shows that planted-fault repairs can depend on numeric traces (low-order bits) rather than understanding. Recommends reporting the weight number format and including a rounded control.

## Replications & Reproductions
- 🧪 **[Qwen 3.8 27B on my laptop can interpret model weights, too](https://simonwillison.net/2026/Nov/3/qwen-can-interpret-model-weights/)**: *Simon Willison*, 3 Nov 2026. A local open-weight model identifies Atari games from raw policy weights using a prompt from the Sparks essay.
- 🧪 **[MatinKhajavi/Weight-Space-Programming](https://github.com/MatinKhajavi/Weight-Space-Programming)**: *Matin Khajavi*. Replicates the eight Sparks experiments with Claude Opus 5.5 and Claude Fable 5.1 instead of GPT-6 Astra.
- 🧪 **[statsleelab/weight_space_programming](https://github.com/statsleelab/weight_space_programming)**: Pure NumPy/SciPy reproduction of all eight Sparks experiments, with a bilingual (EN/KO) interactive guide.

## Community Extensions (Blogs & Code)
- 📝 **[We Asked Opus-5.5 to Edit π0.5's Weights. AutoResearch Made It Happen.](https://cuzyoung.github.io/robotics-weight-editing/en/)**: *Ziyang Gong et al.* Edits a π0.5 vision-language-action robot policy and reports faster real-robot bottle placement at unchanged success.
- 📝 **[Can Opus 5.5 teach an image model what "no" means?](https://sabhyachhabria.com/writing/weight-space-negation/)** *(work in progress)*: *Sabhya Chhabria*, 2 Nov 2026. Edits about 0.02% of Stable Diffusion 3.5 Medium's text-encoder weights to reduce negated objects appearing in images.
- 📝 **[Piano to flute, one weight edit](https://manaskarra.com/blog/magenta-wsp)**: *Manas Karra*, 8 Nov 2026. A single matrix edit to Magenta RealTime's style adapter turns a piano prompt into flute. Judged by the author's own listening.
- 💻 **[brunicardoso/weight-space-programming-genomics](https://github.com/brunicardoso/weight-space-programming-genomics)**: A preregistered, blinded test of whether an LLM agent can detect and repair a planted shortcut in a genomics CNN. Detection was narrowly supported; repair was not.

## Commentary & Critiques
- ⚠️ **[LLMs are not superhuman at reading and writing neural network weights](https://www.seangoedecke.com/llms-are-not-superhuman-at-reading-and-writing-neural-network-weights/)**: *Sean Goedecke*, 3 Nov 2026. Argues that a skilled ML researcher could do the essay's reading tasks and its Qwen fix.
- ⚠️ **[The "Astra can read and write weights to improve Qwen" post is misleading](https://honnibal.dev/blog/astra-read-write-misleading)**: *Matthew Honnibal*, 3 Nov 2026. Argues the essay blurs tool-free reading of raw weights with experiments that use Python or run the network.

## Background: Related Lines of Work
WSP is defined against these older ideas, so they are useful context. They are **not** WSP themselves.

- **Weights as programs:** [Software 2.0](https://karpathy.medium.com/software-2-0-a64152b37c35) (Karpathy, 2017).
- **Program-to-weight compilers:** [Tracr: Compiled Transformers as a Laboratory for Interpretability](https://arxiv.org/abs/2301.05062) (Lindner et al., NeurIPS 2023).
- **Networks that generate weights:** [HyperNetworks](https://arxiv.org/abs/1609.09106) (Ha et al., ICLR 2017); [Neural Network Diffusion](https://arxiv.org/abs/2402.13144) (Wang et al., 2024).
- **Fast-weight programmers:** [Learning to Control Fast-Weight Memories](https://doi.org/10.1162/neco.1992.4.1.131) (Schmidhuber, Neural Computation 1992); [Linear Transformers Are Secretly Fast Weight Programmers](https://arxiv.org/abs/2102.11174) (Schlag et al., ICML 2021).
- **Weight-space learning:** [Equivariant Architectures for Learning in Deep Weight Spaces](https://arxiv.org/abs/2301.12780) (Navon et al., ICML 2023); [Permutation Equivariant Neural Functionals](https://arxiv.org/abs/2302.14040) (Zhou et al., NeurIPS 2023).
- **Algorithmic model editing:** [ROME](https://arxiv.org/abs/2202.05262) (Meng et al., NeurIPS 2022); [MEMIT](https://arxiv.org/abs/2210.07229) (Meng et al., ICLR 2023); [Editing Models with Task Arithmetic](https://arxiv.org/abs/2212.04089) (Ilharco et al., ICLR 2023); [Steering Language Models With Activation Engineering](https://arxiv.org/abs/2308.10248) (Turner et al., 2023).
- **Mechanistic interpretability:** [A Mathematical Framework for Transformer Circuits](https://transformer-circuits.pub/2021/framework/index.html) (Elhage et al., 2021).

---

## Summary Table

| Paper | arXiv | Op. | Domain | Code |
|---|---|---|---|---|
| Sparks of WSP (founding) | blog | R/W/E | RL, diffusion, LLMs | [logs](https://github.com/RikiyaT/lm_understand-logs) |
| Clinical Auditing | [2611.05341](https://arxiv.org/abs/2611.05341) | R/E | Clinical decision nets | [code](https://github.com/hnusrat1/weightspace-rt) |
| WeightLoop | [2611.07319](https://arxiv.org/abs/2611.07319) | E | Scientific predictors | [code](https://github.com/limengran98/WeightLoop) |
| Reasoning vs. Memorization | [2611.08070](https://arxiv.org/abs/2611.08070) | R | CNNs (critique) | [blog](https://sakibbai.com/posts/2026-11-05-llm-weight-space-programming/) |
| IWIBench | [2611.08647](https://arxiv.org/abs/2611.08647) | E | LLM editors → Gemma 3 4B | — |
| Exploring WSP | [2611.09382](https://arxiv.org/abs/2611.09382) | E | Qwen3.5 0.8B/9B | [code](https://github.com/WSP-Scope/WSP-Scope-Project) |
| Quantum VQC | [2611.11537](https://arxiv.org/abs/2611.11537) | W | Quantum circuits | [code](https://github.com/DebarshiKunduPSU/Quantum-Weight-Space-Programming) |
| Policies + Model Checking | [2611.11604](https://arxiv.org/abs/2611.11604) | W/E | Verified RL | [code](https://github.com/LAVA-LAB/COOL-MC/tree/wsp_verified) |
| Medical Imaging | [2611.12066](https://arxiv.org/abs/2611.12066) | W | CNNs, 4 modalities | [code](https://github.com/MaximilianLindholz/weight-space-programming-medical) |
| W-ISA | [2611.13232](https://arxiv.org/abs/2611.13232) | E | LLM runtime | — |
| EEG/ECG | [2611.13758](https://arxiv.org/abs/2611.13758) | W/E | Biosignals | [site](https://daravaram.github.io/BioWSP) |
| Interpretable WSP (iWSP) | [2611.18114](https://arxiv.org/abs/2611.18114) | W | Transformers, brain encoding | [code](https://github.com/csinva/weight-space-programming-autoresearch) |
| WeightBench | [2611.18553](https://arxiv.org/abs/2611.18553) | R/W/E | 2K–7B nets | [code](https://github.com/Aayush-Marasini/WeightBench) |
| Materials Science | [2611.22013](https://arxiv.org/abs/2611.22013) | W | Property predictors | [code](https://github.com/sheikhahnaf/weightspace-programming-for-material-science) |
| No-Transformer | [2611.22055](https://arxiv.org/abs/2611.22055) | W | LLM-designed arch. | [code](https://github.com/effl-lab/Weight-Space-Programming) |
| VLM Repair | [2611.23615](https://arxiv.org/abs/2611.23615) | R/E | VLMs (critique) | — |
| Ethical Priorities | [2611.24330](https://arxiv.org/abs/2611.24330) | E | Text readers | [code](https://github.com/kaiji123/wsp-safety) |
| WeightCode | [2611.25476](https://arxiv.org/abs/2611.25476) | E/W | Seq2seq, ViT, ImageNet | [code](https://github.com/Gen-Verse/WeightCode) |

<sub>Op. = dominant operation: R = read/audit, W = write from scratch, E = edit/repair. Sorted by arXiv ID. Last updated 25 Nov 2026.</sub>

## Open Research Challenges

Important research directions in Weight-Space Programming include:

- **Scalability:** Extending weight-space programming to larger neural networks and foundation models.
- **Reliability:** Evaluating whether weight modifications are reproducible and semantically meaningful.
- **Compositionality:** Combining independently developed weight programs.
- **Interpretability:** Understanding how LLMs reason about neural network parameters.
- **Verification and Safety:** Ensuring weight modifications preserve required model properties.
- **Benchmarking:** Developing standardized evaluations for reading, writing, and editing weights.
- **Applications:** Exploring WSP in robotics, scientific machine learning, vision-language models, and autonomous systems.

Contributions investigating these challenges are welcome.


## Contributing
Pull requests are welcome. To add an entry, include:
1. a link to the paper, post, or repository;
2. a one-line description of what the LLM reads, writes, or edits, and the headline result as the authors state it;
3. code or project links where available.

An entry fits this list if a **general-purpose LLM** decides what to change in a network's weights. Work where a *trained* weight generator or a fixed algorithm does that belongs under [Background](#background-related-lines-of-work).
