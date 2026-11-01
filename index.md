---
layout: default
title: AI Tools Battle
---
<div style="display: flex; align-items: center; gap: 20px;">
  <img src="mlw.png"
       alt="AI Tools Battle Logo"
       width="90"
       style="height: auto;">

  <h1 style="margin: 0;">
    Machine Learning Week Europe 2026
  </h1>
</div>

## Tool Battle: Classical ML vs. Transformers vs. LLM Agents

###Which approach detects fake news best in 60 minutes?

## Competition Overview

Tool Battle is a 60-minute, hands-on competition that compares classical machine learning, transformer models and LLM-based agents on a single task: fake news detection. All participants work with the same dataset and the same time limit, and they are free to choose their own methods and tools.

Can a carefully engineered TF-IDF model still outperform a transformer? Can an LLM agent outperform both? Participants may follow any of these approaches:

- **Classical machine learning.** TF-IDF, SVD, logistic regression, LightGBM and related methods: fast, lightweight and well established, with an emphasis on sound feature engineering.
- **Transformers.** DistilBERT, RoBERTa and similar models, used as embedding extractors or fine-tuned on a free Colab GPU.
- **LLM agents and APIs.** Zero-shot and few-shot prompting, agentic pipelines, and models such as GPT, Claude or Gemini used directly as classifiers, with no training loop required.
- **Hybrid solutions.** Any combination of the approaches above.

Participants may write all of their code themselves or use AI coding assistants such as ChatGPT, Claude Code, Cursor or Codex. AI-assisted development, including vibe coding, is explicitly permitted.

Solutions are ranked on two leaderboards, one for predictive performance and one for analytical quality, so the highest score is not the only route to the top: a clean, well-justified simple model can rank above a more elaborate one.

**Prerequisites:** a laptop, basic Python programming skills, access to Google Colab or an alternative environment for text analytics, such as an LLM API.

## Competition Objective

The primary objective of Tool Battle is to explore how different AI tools, machine learning techniques and analytical approaches can be applied to fake news detection within a limited time.

Participants aim to build an effective fake news detector and to achieve the highest possible **ROC-AUC score**. They may use **any tools, methods or technologies**, including traditional machine learning algorithms, large language models (LLMs), AI coding assistants and other AI-based approaches.

**The competition is not only about achieving the highest ROC-AUC score. It is equally about demonstrating how effectively participants can use modern AI tools to develop, evaluate and explain their solutions.**

## Evaluation Criteria

Submissions are evaluated using **two complementary approaches**, each with its own leaderboard.

### 1. Quantitative Evaluation: ROC-AUC Score

The first evaluation is based on the **ROC-AUC score** calculated from the submitted predictions on the hidden labels of the test dataset. This metric measures how effectively a model distinguishes between fake and non-fake statements. Higher scores indicate better classification performance.

### 2. Qualitative Evaluation: Analysis of Approaches

The second evaluation is based on the submitted `report.txt` files, which are reviewed by an LLM agent under expert supervision. The review assesses:

- The methods, models and tools selected.
- The quality and depth of the fake news detection analysis.
- The correctness of the approach, including the absence of data leakage.
- The validity and interpretation of the reported validation ROC-AUC scores.
- The creativity and effectiveness of the proposed approach.
- The clarity of the explanations and conclusions.

This evaluation recognises not only strong predictive performance but also **innovative, well-reasoned and analytically sound solutions**.

## Data

The competition dataset consists of fake and non-fake statements derived from the well-known [LIAR2 dataset](https://huggingface.co/datasets/chengxuphd/liar2). The original dataset has been simplified into a **binary classification task**, where the target variable `label` indicates whether a statement is fake:

- **1**: fake news
- **0**: not fake news

The data is available at [https://github.com/mlweu2026-tool-battle/data](https://github.com/mlweu2026-tool-battle/data).

## Result Submission

Each participant must submit two files: `submission.csv` and `report.txt`.

#### 1. `submission.csv`: Prediction Results

This file must contain the predicted probability that each statement in the test dataset is fake news.

- The file must have the header `id,prediction`.
- Each prediction must be a probability between **0 and 1**.
- Higher values indicate a greater predicted probability that the statement is fake.
- Predictions must follow the same order as the entries in the test dataset.

```csv
id,prediction
0,0.92
1,0.15
```

#### 2. `report.txt`: Methods and Results

This plain-text file, **no larger than 10 KB**, must briefly describe the participant's approach, including:

- The tools, algorithms and models used for fake news detection.
- The main preprocessing, feature engineering and modelling steps.
- The ROC-AUC scores obtained on the validation dataset.
- Any additional analysis, experiments or improvements performed.
- A brief explanation of the final approach and its results.

Participants are encouraged to describe not only their final solution but also the reasoning behind their methodological choices.

**[Submit your results](https://script.google.com/macros/s/AKfycbxLhtN40Ir_Y1dcfAzv31loGUyacIxop9kv1CvxGqRtSYu2_ZB86EtnYMH6ujv98YTGXw/exec)**

## Leaderboard

The final rankings will appear here once the competition is over.

<!-- MOCK LEADERBOARDS START: delete everything down to MOCK LEADERBOARDS END before publishing real results -->

> **Mock data for layout testing only.** All participants, scores and comments below are fictional and do not reflect real results or the real performance of any method.

### Leaderboard 1: Predictive Performance (ROC-AUC)

| Rank | Participant | Test ROC-AUC |
| :----: | :------------ | -------------: |
| 1 | Elena Marković | **0.8792** |
| 2 | Tomasz Wieczorek | **0.8715** |
| 3 | Sofia Lindqvist | **0.8668** |
| 4 | Matteo Bianchi | 0.8594 |
| 5 | Ingrid Halvorsen | 0.8503 |
| 6 | Luca Moreau | 0.8441 |
| 7 | Anna Kovalenko | 0.8376 |
| 8 | Jonas Becker | 0.8312 |
| 9 | Clara Fernández | 0.8247 |
| 10 | Nikos Papadakis | 0.8139 |
| 11 | Emma van Dijk | 0.7986 |
| 12 | Piotr Zieliński | 0.7901 |
| 13 | Aino Virtanen | 0.7812 |
| 14 | Hugo Laurent | 0.7654 |
| 15 | Daria Petrenko | 0.7423 |

### Leaderboard 2: Analytical Quality (Report Review)

Report scores range from 0 to 100. In the comments, **+** marks a strength and **−** marks a weakness.

| Rank | Participant | Report score | ROC-AUC rank | Comments |
|:----:|:------------|-------------:|:------------:|:---------|
| 1 | Ingrid Halvorsen | **94** | 5 | **+** Clear rationale, documented baselines and stratified cross-validation; validation and test scores differ by only 0.0018.<br>**−** Error analysis is limited to global feature weights. |
| 2 | Elena Marković | **91** | 1 | **+** Out-of-fold stacking prevents leakage; ablation study quantifies each component.<br>**−** Runtime and complexity trade-offs are not discussed. |
| 3 | Sofia Lindqvist | **89** | 3 | **+** Original use of an LLM for interpretable features, with an assessment of their importance.<br>**−** API cost and the stability of generated features are not evaluated. |
| 4 | Anna Kovalenko | **86** | 7 | **+** Compares prompt variants systematically and retrieves examples from training data only.<br>**−** Tuned prompts on a small validation sample, with no confidence intervals. |
| 5 | Tomasz Wieczorek | **83** | 2 | **+** Sound fine-tuning protocol with early stopping and a clear description of the metadata fusion.<br>**−** Offers little interpretation of the errors or the features that drive them. |
| 6 | Jonas Becker | **80** | 8 | **+** Concise, reproducible pipeline with justified SVD and LightGBM settings.<br>**−** Compares only two model configurations. |
| 7 | Aino Virtanen | **77** | 13 | **+** Candid analysis of the limits of zero-shot prompting, with useful probability calibration.<br>**−** Modest performance, and no attempt to use the labelled training data. |
| 8 | Clara Fernández | **74** | 9 | **+** Pragmatic choice for the time limit, with a sensible comparison of embedding models.<br>**−** Metadata fields are ignored without explanation. |
| 9 | Luca Moreau | **71** | 6 | **+** Correct training setup with a clearly reported validation split.<br>**−** Mostly lists steps, with little justification or analysis of the results. |
| 10 | Nikos Papadakis | **67** | 10 | **+** Well-documented prompts and a clear description of the workflow.<br>**−** Probability estimates are uncalibrated, and the choice of examples is not justified. |
| 11 | Piotr Zieliński | **63** | 12 | **+** Simple, transparent baseline that is honestly interpreted.<br>**−** No feature engineering or model comparison beyond the baseline. |
| 12 | Matteo Bianchi | **58** | 4 | **+** Strong test score and detailed feature engineering.<br>**−** Speaker target encoding fitted before the split suggests leakage, which is consistent with a gap of 0.0533 between validation and test scores. |
| 13 | Hugo Laurent | **52** | 14 | **+** Recognises that the one-epoch training is a limitation imposed by the time budget.<br>**−** No baseline or tuning, and the conclusions are not supported by evidence. |
| 14 | Emma van Dijk | **47** | 11 | **+** Creative agent design with a clear architecture description.<br>**−** Web search may retrieve published fact-checks, which is a serious validity risk; the validation score exceeds the test score by 0.0947, and the gap is not investigated. |
| 15 | Daria Petrenko | **38** | 15 | **+** Short and readable, with the prompt included.<br>**−** No validation ROC-AUC is reported, and the choice of method is not explained or analysed. |

<!-- MOCK LEADERBOARDS END -->
