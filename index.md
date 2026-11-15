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
| 1 | user 3 gpu | 0.96703 |
| 2 | Dmytro Khoptii | 0.89721 |
| 3 | Volodymyr Havryliak | 0.89667 |
| 4 | user 2 tr | 0.89239 |
| 5 | Loskutova Anastasiia | 0.88591 |
| 6 | Yan Pekarskyi | 0.88329 |
| 7 | Золочівська А. | 0.88240 |
| 8 | Vitaliy Vasiuk(FEI-42) | 0.87971 |
| 9 | user 1 tifidf | 0.85113 |
| 10 | Demian Pavlyshenko | 0.79009 |
| 11 | Test1 | 0.50000 |

### Leaderboard 2: Analytical Quality (Report Review)

| Report Rank | User | AUC Rank | Comments |
|:--:|:--|:--:|:--|
| 1 | Dmytro Khoptii | 2 | **Approach:** Hybrid rank-averaged ensemble<br>**Methods:** TF-IDF logistic regression, CatBoost, nested target-encoded LightGBM, frozen RoBERTa features, equal rank averaging<br>**Validation:** Five-fold grouped OOF blend AUC 0.8716, fold standard deviation approximately 0.003; strongest individual 0.8648.<br>**Test AUC:** Test 0.89721 exceeds OOF 0.8716; conservative grouped validation and full-data refitting are plausible contributors, not proof against leakage.<br>**+** Duplicate-grouped folds and nested target encoding/stacked scores provide particularly strong validation safeguards.<br>**+** Clear ablations, resource constraints, contamination awareness, and correct distinction between ranks and calibrated probabilities.<br>**−** Blend selection reuses OOF results without an independent final evaluation.<br>**−** Random-date validation leaves temporal and unseen-source robustness untested. |
| 2 | Volodymyr Havryliak | 3 | **Approach:** Hybrid stacked ensemble<br>**Methods:** Late-fusion DeBERTa, DistilBERT, sparse linear models, metadata boosting, temporal target encoding, logistic stacking<br>**Validation:** Five-fold OOF: DeBERTa 0.8749; stack diagnostic 0.8781; predicted test range 0.873–0.878.<br>**Test AUC:** Test 0.89667 exceeds diagnostic 0.8781 and forecast ceiling; strong generalisation, but claimed bounds are not statistically justified.<br>**+** Detailed architecture, ablations, coefficients, and explicit disclosure of stacking optimism.<br>**+** Fold-aware temporal encoding and shuffled-label diagnostics demonstrate substantial leakage awareness.<br>**−** Reused base OOF predictions prevent unbiased meta-validation; a different split seed does not resolve dependence.<br>**−** Leak-free conclusions overreach: shuffle results omit transformer learners despite claiming full-pipeline checks. |
| 3 | Loskutova Anastasiia | 5 | **Approach:** Classical ML<br>**Methods:** Multi-field word/character TF-IDF and categorical metadata; regularised logistic regression<br>**Validation:** Holdout AUC 0.8705; five-fold CV 0.8667 ± 0.0032; statement baseline 0.8117.<br>**Test AUC:** Test 0.88591 modestly exceeds CV 0.8667; no observed overfitting gap, although shared-data model selection adds optimism.<br>**+** Strong ablations and coefficient interpretation explain lexical versus metadata contributions.<br>**+** Fold-local preprocessing and candid disclosure of tuning reuse support methodological transparency.<br>**−** No duplicate-grouped or temporal evaluation tests transfer beyond the random split.<br>**−** Absence of target encoding alone does not establish absence of all target leakage. |
| 4 | user 3 gpu | 1 | **Approach:** Zero-shot LLM classification<br>**Methods:** GPT API scores statement and metadata using internal knowledge; numeric output interpreted as fake probability<br>**Validation:** No independent validation; claims labelled-test AUC 0.96529.<br>**Test AUC:** Organiser test 0.96703 matches claimed test 0.96529; absent independent validation, memorisation or test-label access remains unresolved.<br>**+** Best hidden-test ranking by a substantial margin.<br>**+** Explicitly acknowledges pretraining contamination and contradictory prompt polarity.<br>**−** Claimed access to labelled test statements raises serious evaluation-integrity concerns.<br>**−** Conflicting probability instructions and missing exact prompt/API settings undermine reproducibility. |
| 5 | user 2 tr | 4 | **Approach:** Fine-tuned transformer ensemble<br>**Methods:** DeBERTa-v3-small and DistilBERT on statement plus metadata; equal probability averaging<br>**Validation:** Stratified holdout AUC: DeBERTa 0.86972; DistilBERT 0.86510; ensemble not evaluated.<br>**Test AUC:** Test ensemble 0.89239 exceeds individual validation scores; ensemble benefit and split variability are plausible, not evidence of leakage.<br>**+** Reproducible training configuration with sensible numerical-stability adjustments.<br>**+** Complementary pretrained models achieve strong hidden-test performance.<br>**−** Submitted ensemble lacks a directly comparable validation score.<br>**−** Single checkpoint-selection split; no ablations, duplicate checks, or contamination discussion. |
| 6 | Vitaliy Vasiuk(FEI-42) | 8 | **Approach:** Hybrid feature engineering and classical ML<br>**Methods:** XGBoost combines TF-IDF, MiniLM embeddings, pretrained linguistic features, extracted speaker profiles, and temporal speaker history<br>**Validation:** Selected XGBoost: CV AUC 0.861, holdout 0.873; scratch transformer validation 0.848, holdout 0.838.<br>**Test AUC:** Organiser test 0.87971 agrees reasonably with holdout 0.873; CV 0.861 is lower, without obvious test deterioration.<br>**+** Extensive feature-group ablations and model comparisons quantify small gains honestly.<br>**+** Evidence-constrained profile extraction and analysis of scratch-transformer failure show thoughtful experimentation.<br>**−** Reported six-to-seven-hour development exceeds the competition's sixty-minute allowance.<br>**−** Holdout guides model choice; history encoding's fold isolation remains unclear despite chronological ordering. |
| 7 | Золочівська А. | 7 | **Approach:** Classical ML<br>**Methods:** Word and character TF-IDF over statements and selected metadata; L2 logistic regression<br>**Validation:** Stratified 80/20 holdout: ROC-AUC 0.8560; accuracy 0.7700.<br>**Test AUC:** Test 0.8824 exceeds validation 0.8560; full-data refitting and sampling variability are plausible, with no obvious leakage signal.<br>**+** Explicit fold-local feature fitting, target exclusion, and deterministic validation.<br>**+** Clear final refitting and positive-class probability generation.<br>**−** Single holdout without uncertainty estimates or duplicate controls.<br>**−** No ablations substantiate feature exclusions or word/character complementarity. |
| 8 | Yan Pekarskyi | 6 | **Approach:** Classical ML ensemble<br>**Methods:** Multi-field word/character TF-IDF, smoothed target encoding, logistic regression, ComplementNB, and log-loss SGD blending<br>**Validation:** not reported<br>**Test AUC:** Test 0.88329 is competitive, but missing validation metrics prevent assessing the generalisation gap or supporting leakage claims.<br>**+** Detailed feature specifications, category statistics, and submission-integrity checks.<br>**+** Diverse inexpensive classifiers produce competitive hidden-test ranking.<br>**−** Target encoding nesting and fold-local text fitting are insufficiently specified to establish leakage-free evaluation.<br>**−** Claims calibration without calibration metrics; lengthy descriptive statistics substitute for model comparisons and validation results. |
| 9 | user 1 tifidf | 9 | **Approach:** Classical ML<br>**Methods:** Concatenated statement and metadata word TF-IDF, classified with LightGBM<br>**Validation:** Single 85/15 holdout ROC-AUC: 0.85157.<br>**Test AUC:** Test 0.85113 closely matches validation 0.85157; no performance discrepancy suggesting overfitting or leakage.<br>**+** Explicit training-only vectorizer fitting and reproducible feature/model settings.<br>**+** Fast, straightforward baseline with credible evaluation.<br>**−** Single split; stratification, uncertainty, and duplicate handling are unspecified.<br>**−** Metadata benefit is asserted without ablations or error analysis. |
| 10 | Demian Pavlyshenko | 10 | **Approach:** Classical ML<br>**Methods:** Field-specific TF-IDF and metadata logistic regression; statement-only and LightGBM comparisons<br>**Validation:** Five-fold AUC: final 0.858 ± 0.008; text-only 0.812; LightGBM 0.840; final accuracy 0.774.<br>**Test AUC:** Test 0.790 substantially trails CV 0.858; reported thresholding could explain lost ranking information, rather than leakage.<br>**+** Clear dataset exploration identifies temporal drift, source priors, and duplicate statements.<br>**+** Useful baselines, fold results, hyperparameters, and explicit generalisation limitations.<br>**−** Thresholded final predictions are inappropriate for preserving ROC-AUC ranking.<br>**−** Fold-local vectorizer fitting is unspecified; random CV does not isolate duplicate or speaker overlap. |
| 11 | Test1 | 11 | **Approach:** Undocumented<br>**Methods:** No identifiable models or features<br>**Validation:** not reported<br>**Test AUC:** Test AUC 0.500 indicates chance-level ranking; no validation comparison possible.<br>**−** Meaningless report provides no reproducible method or analysis.<br>**−** No validation, leakage controls, or conclusions. |
