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

## Tool Battle: Classical ML vs. Transformers vs. LLM Agents - Which approach detects fake news best in 60 minutes?

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

### Leaderboard 1: Predictive Performance (ROC-AUC)

| AUC Rank | User | AUC |
|:--:|:--|--:|
| 1 | Dean Abbott | 0.89555 |
| 2 | Nina | 0.88019 |
| 3 | Martin Szugat Submission #1 | 0.87081 |
| 4 | Simcha | 0.86346 |

### Leaderboard 2: Analytical Quality (Report Review)

| Report Rank | User | AUC Rank | Comments |
|:--:|:--|:--:|:--|
| 1 | Dean Abbott | 1 | **Approach:** Classical machine learning ensemble<br>**Methods:** Bagged logistic regression and LightGBM; word/character TF-IDF, metadata, SVD/NMF, out-of-fold target encodings, and neighbor fake rates.<br>**Validation:** OOB-averaged ROC-AUC: LR 0.8667; LightGBM 0.8596; ensemble 0.8699; text-only 0.8094.<br>**Test AUC:** Best test 0.89555 exceeds OOB 0.8699 by 0.02565; favorable generalization, but uncertainty estimates do not explain this gap.<br>**+** Exceptionally thorough paired experiments, ablations, subgroup diagnostics, and explicit source-shortcut analysis.<br>**+** Careful bootstrap duplicate handling and reported out-of-fold label-derived features support methodological soundness.<br>**−** Train-plus-test text preprocessing is transductive and exposes OOB inputs, although not labels.<br>**−** Repeated OOB model selection introduces optimism; bootstrap ranges are not formal test-performance confidence intervals. |
| 2 | Nina | 2 | **Approach:** Classical machine learning ensemble<br>**Methods:** Equal-weight logistic regression ensemble combining metadata-enriched word TF-IDF with statement TF-IDF and scaled one-hot categorical features.<br>**Validation:** Holdout ROC-AUC: text 0.81189; metadata variants 0.85397–0.86177; ensemble 0.86462.<br>**Test AUC:** Second-best test 0.88019 exceeds validation 0.86462 by 0.01557; no clear overfitting or leakage signal.<br>**+** Clearly specified models and training-fold-only preprocessing make the procedure reproducible.<br>**+** Explicitly acknowledges selection optimism, source correlations, and the distinction between prediction and factual verification.<br>**−** Final models retain only 8,000 training rows rather than refitting on all available labels.<br>**−** One repeatedly consulted random split; no grouped or chronological robustness evaluation. |
| 3 | Martin Szugat Submission #1 | 3 | **Approach:** Classical machine learning<br>**Methods:** Custom browser-based logistic regression using word TF-IDF, metadata tokens, and simple statement features.<br>**Validation:** Holdout ROC-AUC: unigrams 0.7764; bigrams 0.7867; metadata/final 0.8619.<br>**Test AUC:** Test 0.87081 modestly exceeds validation 0.8619; consistent performance, without obvious overfitting evidence.<br>**+** Explicit training-only preprocessing and reproducible implementation details.<br>**+** Clear ablations, coefficient interpretation, and candid discussion of speaker dependence.<br>**−** Single random holdout cannot establish generalization across speakers or time.<br>**−** Strong metadata shortcuts, including 'fake' descriptions, warrant provenance checks. |
| 4 | Simcha | 4 | **Approach:** Hybrid classical machine learning and transformer embeddings<br>**Methods:** Logistic regression on word/character TF-IDF and mean-pooled DistilBERT embeddings; validation-tuned weighted probability ensemble.<br>**Validation:** ROC-AUC: TF-IDF 0.81379; transformer embeddings 0.82128; ensemble 0.83310.<br>**Test AUC:** Test 0.86346 exceeds validation 0.83310 by 0.03036; encouraging, but unspecified validation prevents diagnosing the gap.<br>**+** Complementary lexical and pretrained semantic representations provide a sensible ensemble.<br>**+** Component scores demonstrate an ensemble improvement over both individual models.<br>**−** Validation split, preprocessing isolation, hyperparameters, and final training procedure are unspecified.<br>**−** No error analysis, leakage discussion, or assessment of ensemble-weight selection optimism. |

