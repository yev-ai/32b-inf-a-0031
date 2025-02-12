## THIS IS A PUBLIC FORK.
[@mle](https://github.com/orgs/yev-ai/teams/mle) [@mlr](https://github.com/orgs/yev-ai/teams/mlr) Feel free to test it, improve it, and submit contributions upstream.

Do not use any of our ongoing R&D and don't push this model beyond:
  - 89.0 Math500
  - 46.0 AIME2024
  - 90.0 LiveCodeBench-Easy
  - 60.0 LiveCodeBench-Medium
  - 22.5 LiveCodeBench-Hard
  - 61.0 GPQA-Diamond
  - 64.0 OlympiadBench (M/EN)
  - 82.5 MMLU 0-shot, no CoT
  - 86.5 MMLU 5-shot, no CoT
  - 55.0 ARC-C 0-shot, no CoT
  - 80.0 IFEval
  - 45.0 MGSM 0-shot, direct
  - 65.0 MGSM 8-shot, direct
  - 57.5 BFCL-v3
  - 80.0 Arena-Hard

If you're pushing it beyond these limits, use DVC and provision [@mlops](https://github.com/orgs/yev-ai/teams/mlops) in UltraCluster us-east-1:c. 

Relevant info:
  - [Sky T1 Paper](https://github.com/yev-ai/32b-inf-a-0031/blob/main/papers/sky-t1.pdf): That's this thing.
  - [LIMO Paper](https://github.com/yev-ai/32b-inf-a-0031/blob/main/papers/limo.pdf) and [GitHub](https://github.com/GAIR-NLP/LIMO/tree/main): signal to noise ratio is important and less data is better.
  - [S1 Paper](https://github.com/yev-ai/32b-inf-a-0031/blob/main/papers/s1.pdf): don't use shit data and keep doing the basic prompt rewrites / appends that our runtimes do.
  - [ReasonFlux Paper](https://github.com/yev-ai/32b-inf-a-0031/blob/main/papers/reason-flux.pdf): same theme, quality data / cognitive templates / hierarchical reinforcement learning seqs.
  - [SGFT Paper](https://github.com/yev-ai/32b-inf-a-0031/blob/main/papers/slm-guidance.pdf): SLMs continue to dominate as domain experts, this is conceptually similar to our orchestrator tbh.
  - [COAT Paper](https://github.com/yev-ai/32b-inf-a-0031/blob/main/papers/coat.pdf): What CoT should've been, MCTS memory bolt-on, larger token search space without more data.
  - [Context n Math Paper](https://github.com/yev-ai/32b-inf-a-0031/blob/main/papers/context-math-reason.pdf): thing that further helps us purge shit data called LMS3. We like less, and we like better.
  - [SLM COT Paper](https://github.com/yev-ai/32b-inf-a-0031/blob/main/papers/slm-cot.pdf): shocker, distilling process beats distilling answers and adversarial fine-tuning stops overfitting.


For the lulz
  - [DSR1 Paper](https://github.com/yev-ai/32b-inf-a-0031/blob/main/papers/dsr1.pdf): Recommended for friday night bingo. Read this if you want a free 6-pack. Otherwise useless.
  - [TAD LLM](https://github.com/yev-ai/32b-inf-a-0031/blob/main/papers/tad-llm.pdf): how to get shit data. read it, have a laugh, recommend it to our competitors. /popcorn