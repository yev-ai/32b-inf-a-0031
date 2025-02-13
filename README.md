# From [SkyThought](https://github.com/NovaSky-AI/SkyThought)
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



# From  [Us](https://www.yev.ai/)
**This model fork is currently WIP and may be unstable.**
### Relevant:
  - [LIMO Paper](https://github.com/yev-ai/32b-inf-a-0031/blob/main/papers/limo.pdf) and [GitHub](https://github.com/GAIR-NLP/LIMO/tree/main): 💅MOOD SETTER💅 - snr matters lots, less data is better, cognitive templates r gud.
  - [Sky T1 Paper](https://github.com/yev-ai/32b-inf-a-0031/blob/main/papers/sky-t1.pdf): That's this thing. ST team is good. We like ST. If we see ST, we buy them a drink of their choice.
  - [COAT Paper](https://github.com/yev-ai/32b-inf-a-0031/blob/main/papers/coat.pdf): What CoT should've been, MCTS memory bolt-on, larger token search space without more data.
  - [SLM COT Paper](https://github.com/yev-ai/32b-inf-a-0031/blob/main/papers/slm-cot.pdf): Shocker, distilling process beats distilling answers and adversarial fine-tuning stops overfitting.
  - [S1 Paper](https://github.com/yev-ai/32b-inf-a-0031/blob/main/papers/s1.pdf): Don't use 💩 data and keep doing the basic prompt rewrites and appends that our runtimes do.
  - [ReasonFlux Paper](https://github.com/yev-ai/32b-inf-a-0031/blob/main/papers/reason-flux.pdf): Same theme, quality data / cognitive templates / hierarchical reinforcement learning seqs.
  - [SGFT Paper](https://github.com/yev-ai/32b-inf-a-0031/blob/main/papers/slm-guidance.pdf): SLMs continue to dominate as domain experts, this is conceptually similar to our orchestrator tbh.
  - [Context n Math Paper](https://github.com/yev-ai/32b-inf-a-0031/blob/main/papers/context-math-reason.pdf): Thing that further helps us purge 💩 data called LMS3. We like less, and we like better.


### Just Because:
  - [DSR1 Paper](https://github.com/yev-ai/32b-inf-a-0031/blob/main/papers/dsr1.pdf): Nothing new. Read this if you want a free 6-pack. Recommended for friday night bingo. 
  - [TAD LLM](https://github.com/yev-ai/32b-inf-a-0031/blob/main/papers/tad-llm.pdf): How to get 💩 data - read it, laugh, and go convince our competitors to do this for a bonus.

[@mle](https://github.com/orgs/yev-ai/teams/mle) [@mlr](https://github.com/orgs/yev-ai/teams/mlr) Feel free to test it, improve it, and submit contributions upstream.

### But Seriously, Why?
It's public demo time! Make it cool, don't implement our SoTA R&D for now. Limiter table:

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


All variants exceeding the ceilings specified for 32b-inf-a-0031 belong in [32b-inf-a-0032](https://github.com/yev-ai/32b-inf-a-0032).

Provision [@mlops](https://github.com/orgs/yev-ai/teams/mlops) in UltraCluster us-east-1:c. 