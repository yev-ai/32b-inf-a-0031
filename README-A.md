<div align="center">

# SkyThought

[![Github](https://img.shields.io/badge/SkyThought-000000?style=for-the-badge&logo=github&logoColor=000&logoColor=white)](https://github.com/NovaSky-AI/SkyThought) [![Twitter](https://img.shields.io/badge/NovaSky-white?style=for-the-badge&logo=X&logoColor=000&color=000&labelColor=white)](https://x.com/NovaSkyAI) [![Hugging Face Collection](https://img.shields.io/badge/NovaSky-fcd022?style=for-the-badge&logo=huggingface&logoColor=000&labelColor)](https://huggingface.co/NovaSky-AI) [![Discord](https://img.shields.io/badge/NovaSky-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/RBAjeWSA)


<div align="center" style="font-family: Arial, sans-serif;">
  <p>
    <a href="#news" style="text-decoration: none; font-weight: bold;">News</a> •
    <a href="#links" style="text-decoration: none; font-weight: bold;">Links</a> •
    <a href="#getting-started" style="text-decoration: none; font-weight: bold;">Getting Started</a> •
    <a href="#evaluation" style="text-decoration: none; font-weight: bold;">Evaluation</a> •
    <a href="#citation" style="text-decoration: none; font-weight: bold;">Citation</a> •
    <a href="#acknowledgement" style="text-decoration: none; font-weight: bold;">Acknowledgement</a> 
  </p>
</div>

</div>


# News
- **[2025/01/23]** ⚡️ We released Sky-T1-32B-Flash ([model](https://huggingface.co/NovaSky-AI/Sky-T1-32B-Flash), [data](https://huggingface.co/datasets/NovaSky-AI/Sky-T1_preference_data_10k)) to tackle overthinking and reduce reasoning sequence lengths while maintaining accuracy.
- **[2025/01/19]** 🎉 [Chat demo](http://164.152.23.196:3000/) for Sky-T1-32B-Preview is alive! Please check it out!
- **[2025/01/10]** 🎉 We have released our Sky-T1-32B-Preview [model](https://huggingface.co/NovaSky-AI/Sky-T1-32B-Preview) and [data](https://huggingface.co/datasets/NovaSky-AI/Sky-T1_data_17k) through [HuggingFace](https://huggingface.co/NovaSky-AI)!


# Links

- 📜 [Sky-T1-32B-Flash Blog Post](https://novasky-ai.github.io/posts/reduce-overthinking/)
- 📜 [Sky-T1-32B-Preview model Blog Post](https://novasky-ai.github.io/posts/sky-t1/)
- 🤗 [Sky-T1-32B-Preview model](https://huggingface.co/NovaSky-AI)

# Getting Started

We open source the code and scripts we used for data curation, training, and evaluation for Sky-T1-32B-Preview, you can find more details in each directory.
- [`recipes`](./recipes/): Recipes - data curation steps and training strategies - for building our models `Sky-T1-32B-Flash` and `Sky-T1-32B-Preview`. 
- [`skythought/skythought_evals`](./skythought/skythought_evals/): Our data generation and evaluation library. 
- [`skythought/train`](./skythought/train/): Training scripts for Sky-T1. We use [Llama-Factory](https://github.com/hiyouga/LLaMA-Factory) to perform training. 


# Evaluation

## Usage

First, clone the repository and install the package

```shell
git clone https://github.com/NovaSky-AI/SkyThought.git
cd SkyThought
# installs shown for conda
conda create -n eval python==3.10
conda activate eval 
pip install -e .
```

We support a wide variety of datasets in mathematics, science and coding:

- AIME'24
- MATH500
- GPQADiamond
- MMLU
- ARC-Challenge
- OlympiadBench
- AMC'23 
- TACO 
- APPS
- LiveCodeBench
- MMLU Pro
- MinervaMath
- GSM8K

For running evaluation, please refer to [skythought_evals/README.md](skythought/skythought_evals/README.md).


### Evaluation results
Following, we show our evaluation results for the Sky-T1-32B-Preview model across math, coding, and science benchmarks.

| Metric                | Sky-T1-32B-Preview | Qwen-2.5-32B-Instruct | QwQ   | o1-preview |
|-----------------------|---------------------|--------|-------|------------|
| Math500              | 86.4                    | 81.4    | 92.2 | 81.4       |
| AIME2024             | 43.3                    | 16.7    | 50.0  | 40.0       |
| LiveCodeBench-Easy   | 86.3                    | 84.6   | 90.7  | 92.9       |
| LiveCodeBench-Medium | 56.8                    | 40.8   | 56.3  | 54.9       |
| LiveCodeBench-Hard   | 17.9                    | 9.8   | 17.1  | 16.3       |
| GPQA-Diamond         | 56.8                    | 45.5   | 52.5  | 75.2       |
| OlympiadBench (Math, EN)    | 59.79	           | 46.74	| 62.17	 | 59.2      | 

We also evaluate on non-reasoning benchmarks (these are benchmarks for instruction-following, QA, etc) to test whether the model has traded-off capability in other domains for better performance in reasoning-related benchmarks. 

| Metric | Sky-T1-32B-Preview | Qwen-2.5-32B-Instruct | QwQ-32B-Preview | Eval Implementation |
|---------|-------------------|---------------------|-----------------|-------------------|
| MMLU (0 shot; no CoT) | **78.36** | 74.14 | 71.23 | [lm_eval](https://github.com/EleutherAI/lm-evaluation-harness) |
| MMLU (5 shot; no CoT) | 82.46 | **82.62** | 82.32 | [lm_eval](https://github.com/EleutherAI/lm-evaluation-harness) |
| ARC-C (0 shot; no CoT) | **49.49** | 49.4 | 49.66 | [lm_eval](https://github.com/EleutherAI/lm-evaluation-harness) |
| IFEval | 75.79 | **78.74** | 42.51 | [lm_eval](https://github.com/EleutherAI/lm-evaluation-harness) |
| LLM-as-a-Judge | 9.12	| **9.19** | 8.30 | [fastchat](https://github.com/lm-sys/FastChat/tree/main/fastchat/llm_judge) |
| MGSM (0 shot; `direct`) | 33 | **42.3** | 19.07 | [lm_eval](https://github.com/EleutherAI/lm-evaluation-harness) |
| MGSM (8-shot; `direct`) | 58.4 | **61.47** | 58.5 | [lm_eval](https://github.com/EleutherAI/lm-evaluation-harness) |
| BFCL-v3 | 53.18 | **58.92** | 17.41 | [BFCL](https://github.com/ShishirPatil/gorilla/tree/main/berkeley-function-call-leaderboard) |
| Arena-Hard | **74.79** | 66.51 | 52.6 | [Arena-Hard-Auto](https://github.com/lmarena/arena-hard-auto) |

| Acknowledgement |
| --------------- |

This work is done at [Berkeley Sky Computing Lab](https://sky.cs.berkeley.edu/), with the amazing compute support from [Lambda Labs](https://lambdalabs.com/service/gpu-cloud?srsltid=AfmBOop5FnmEFTkavVtdZDsLWvHWNg6peXtat-OXJ9MW5GMNsk756PE5), [Anyscale](https://www.anyscale.com/), and [Databricks](https://www.databricks.com/). We would like to express our gratitude for the valuable academic feedback and support from the [Still-2 Team](https://arxiv.org/pdf/2412.09413), and Junyang Lin from the [Qwen Team](https://qwenlm.github.io/).

# From  Yevai
This model fork is WIP and may be unstable. We make no quality or availability guarantees at this time.
### Relevant:
  - [Sky T1 Paper](https://github.com/yev-ai/32b-inf-a-0031/blob/main/papers/sky-t1.pdf): That's this thing.
  - [LIMO Paper](https://github.com/yev-ai/32b-inf-a-0031/blob/main/papers/limo.pdf) and [GitHub](https://github.com/GAIR-NLP/LIMO/tree/main): 💅MOOD SETTER💅 - snr matters lots, less data is better, cognitive templates r gud.
  - [COAT Paper](https://github.com/yev-ai/32b-inf-a-0031/blob/main/papers/coat.pdf): What CoT should've been, MCTS memory bolt-on, larger token search space without more data.
  - [SLM COT Paper](https://github.com/yev-ai/32b-inf-a-0031/blob/main/papers/slm-cot.pdf): Shocker, distilling process beats distilling answers and adversarial fine-tuning stops overfitting.
 - [S1 Paper](https://github.com/yev-ai/32b-inf-a-0031/blob/main/papers/s1.pdf): Don't use shit data and keep doing the basic prompt rewrites / appends that our runtimes do.
  - [ReasonFlux Paper](https://github.com/yev-ai/32b-inf-a-0031/blob/main/papers/reason-flux.pdf): Same theme, quality data / cognitive templates / hierarchical reinforcement learning seqs.
  - [SGFT Paper](https://github.com/yev-ai/32b-inf-a-0031/blob/main/papers/slm-guidance.pdf): SLMs continue to dominate as domain experts, this is conceptually similar to our orchestrator tbh.
  - [Context n Math Paper](https://github.com/yev-ai/32b-inf-a-0031/blob/main/papers/context-math-reason.pdf): Thing that further helps us purge shit data called LMS3. We like less, and we like better.


### Just Because:
  - [DSR1 Paper](https://github.com/yev-ai/32b-inf-a-0031/blob/main/papers/dsr1.pdf): Nothing new. Read this if you want a free 6-pack. Recommended for friday night bingo. 
  - [TAD LLM](https://github.com/yev-ai/32b-inf-a-0031/blob/main/papers/tad-llm.pdf): How to get shit data - read it, laugh, go convince our competitors to do this for a bonus.


[@mle](https://github.com/orgs/yev-ai/teams/mle) [@mlr](https://github.com/orgs/yev-ai/teams/mlr) Feel free to test it, improve it, and submit contributions upstream.

### But Seriously, Why?
We're overdue for a public demo. Make it cool, don't implement our current SoTA R&D. Limiter table:

| Metric Ceiling        | Sky-T1-32B-Preview | 32b-inf-a-0031 | 32b-inf-a-0032 |
|-----------------------|---------------------|-------|---------------------|
| Math500              | 86.40                    | 92.00 | N/A |
| AIME2024             | 43.30                    | 50.00 | N/A |
| LiveCodeBench-Easy   | 86.30                    | 92.00 | N/A |
| LiveCodeBench-Medium | 56.80                    | 59.00 | N/A |
| LiveCodeBench-Hard   | 17.90                    | 19.00 | N/A |
| GPQA-Diamond         | 56.80                    | 75.00 | N/A |
| OlympiadBench (Math, EN)    | 59.79	            | 62.00 | N/A |
| MMLU (0 shot; no CoT) | 78.36 | 80.00 | N/A |
| MMLU (5 shot; no CoT) | 82.46 | 85.00 | N/A |
| ARC-C (0 shot; no CoT) | 49.49 | 65.00 | N/A |
| IFEval | 75.79 | 80.00 | N/A |
| LLM-as-a-Judge | 09.12 | 09.50 | N/A |
| MGSM (0 shot; `direct`) | 33.00 | 45.00 | N/A |
| MGSM (8-shot; `direct`) | 58.40 | 62.50 | N/A |
| BFCL-v3 | 53.18 | 60.00 | N/A |
| Arena-Hard | 74.79 | 80.00 | N/A |


For now, all variants exceeding ceilings specified for 32b-inf-a-0031 belong in [32b-inf-a-0032](https://github.com/yev-ai/32b-inf-a-0032).

Provision [@mlops](https://github.com/orgs/yev-ai/teams/mlops) in UltraCluster us-east-1:c. 

