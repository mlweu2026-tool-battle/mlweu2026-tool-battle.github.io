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
| 1 | Martin Szugat Submission #2 | 0.96649 |
| 2 | Timotej Giacomelli | 0.95547 |
| 3 | Matthias Göbel | 0.89830 |
| 4 | Dean Abbott | 0.89555 |
| 5 | whistleblower | 0.89388 |
| 6 | Nina 2 | 0.89024 |
| 7 | Sü Suri | 0.88153 |
| 8 | Nina | 0.88019 |
| 9 | Romina Mirshekar | 0.87862 |
| 10 | Martin Szugat Submission #1 | 0.87081 |
| 11 | Simcha | 0.86346 |

### Leaderboard 2: Analytical Quality (Report Review)

| Report Rank | User | AUC Rank | Comments |
|:--:|:--|:--:|:--|
| 1 | Matthias Göbel | 3 | **Approach:** Hybrid sparse features and frozen transformer embeddings<br>**Methods:** Joint logistic regression over word/character TF-IDF, encoded metadata, and weighted e5-small-v2 embeddings.<br>**Validation:** Five-fold OOF AUC 0.8731; temporal 0.8915; speaker-grouped 0.8584; baseline OOF 0.8663.<br>**Test AUC:** Test 0.89830 exceeds OOF 0.8731 and approaches temporal 0.8915; strong performance without an obvious leakage-driven discrepancy.<br>**+** Exceptional ablations, harder validation splits, uncertainty analysis, and explicit correction of earlier results.<br>**+** Careful cross-fitting controls and unusually candid discussion of source priors, memorisation, and selection bias.<br>**−** Extensive configuration searches reuse the same folds; no untouched estimate.<br>**−** Next-steps section inconsistently lists larger encoders and boosting already reported as tried. |
| 2 | Timotej Giacomelli | 2 | **Approach:** LLM-led hybrid rank ensemble<br>**Methods:** Claude Opus few-shot scoring blended with Sonnet, fine-tuned RoBERTa, frozen MPNet, and classical text/metadata models.<br>**Validation:** Holdout AUC: Opus 0.9501; RoBERTa 0.8783; classical/transformers 0.8837; final 0.9557.<br>**Test AUC:** Test 0.95547 almost exactly matches validation 0.9557; supports consistency, but cannot exclude public-data memorisation.<br>**+** Extensive component comparisons, complementarity analysis, and blend-weight sensitivity checks.<br>**+** Transparent disclosure of possible pretrained contamination and differing final training procedures.<br>**−** Public PolitiFact exposure could explain substantial LLM gains; no contamination-controlled evaluation.<br>**−** Many models and blend choices share one holdout; exact prompts and model versions are absent. |
| 3 | Dean Abbott | 4 | **Approach:** Classical machine-learning ensemble with bootstrap bagging<br>**Methods:** Bagged TF-IDF logistic regression and LightGBM using SVD/NMF topics, cross-fitted target rates, nearest-neighbor rates, and metadata.<br>**Validation:** OOB-average AUC: logistic 0.8667; LightGBM 0.8596; final blend 0.8699; text-only 0.8094.<br>**Test AUC:** Test 0.89555 exceeds OOB 0.8699; no observed generalization collapse, although transductive preprocessing weakens strict OOB independence.<br>**+** Outstanding ablations, paired comparisons, subgroup diagnostics, and source-shortcut interpretation.<br>**+** Transparent bootstrap weighting and safeguards against duplicate-row target leakage.<br>**−** TF-IDF and topic models include OOB and test text, introducing disclosed unsupervised transductive contamination.<br>**−** Repeated OOB-driven experimentation creates selection optimism; no untouched or source-disjoint evaluation. |
| 4 | whistleblower | 5 | **Approach:** Hybrid lexical and transformer-based ensemble<br>**Methods:** TF-IDF logistic regression blended with Random Forest using frozen-BERT neural-head scores, cross-fitted source rates, and style features.<br>**Validation:** Five-fold mean AUC: logistic 0.8594±0.0090; forest 0.8567±0.0082; blend 0.8656±0.0088.<br>**Test AUC:** Test 0.89388 exceeds validation 0.8656; strong result, with reported cross-fitting reducing obvious supervised leakage risks.<br>**+** Careful nested group cross-fitting protects stacked predictions and target-rate features.<br>**+** Reports fold variability and consistent blend improvements; removes exact train–test statement matches.<br>**−** Exploratory selection still reuses outer-fold results; no independent final assessment.<br>**−** No source-disjoint or temporal evaluation, and limited discussion of pretrained contamination. |
| 5 | Martin Szugat Submission #2 | 1 | **Approach:** Zero-shot LLM and classical machine-learning blend<br>**Methods:** Equal-weight probability blend of an unspecified gateway LLM and custom TF-IDF logistic regression with metadata.<br>**Validation:** Linear holdout 0.8798; 200-row subset: linear 0.8702, LLM 0.9739, blend 0.9726.<br>**Test AUC:** Best test AUC 0.96649 broadly matches subset blend 0.9726; small-sample uncertainty and pretrained memorisation remain unresolved.<br>**+** Strong hidden-test discrimination supports the hybrid's practical effectiveness.<br>**+** Same-row component comparison clearly identifies the source of the performance improvement.<br>**−** LLM identity, prompt, subset selection, and contamination checks are missing.<br>**−** Conclusion contradicts the submitted blend; claimed browser-only deterministic approach is outdated. |
| 6 | Nina 2 | 6 | **Approach:** Classical machine-learning ensemble<br>**Methods:** Equal-weight logistic-regression ensemble combining metadata-as-text TF-IDF and statement TF-IDF with categorical one-hot features.<br>**Validation:** Holdout AUC: text 0.81189; metadata models 0.85397–0.86177; ensemble 0.86462.<br>**Test AUC:** Test 0.89024 exceeds validation 0.86462 by 0.02562; not evidence of leakage alone, but unexplained by this report.<br>**+** Detailed, reproducible pipeline description with explicit training-fold preprocessing.<br>**+** Strong discussion of dataset shortcuts and the limits of random-split evaluation.<br>**−** Identical report to submission 1 does not explain the different submitted predictions.<br>**−** Single-holdout selection and no full-data refit limit methodological strength. |
| 7 | Nina | 8 | **Approach:** Classical machine-learning ensemble<br>**Methods:** Equal-weight logistic-regression ensemble combining metadata-as-text TF-IDF and statement TF-IDF with categorical one-hot features.<br>**Validation:** Holdout AUC: text 0.81189; metadata models 0.85397–0.86177; ensemble 0.86462.<br>**Test AUC:** Test 0.88019 exceeds validation 0.86462 modestly; no clear evidence of harmful overfitting or label leakage.<br>**+** Clear preprocessing isolation, model specifications, and comparative experiments.<br>**+** Thoughtful discussion of source shortcuts, correlated records, and selection optimism.<br>**−** All model comparisons use one random holdout; source-disjoint generalization remains untested.<br>**−** Final models retain only 8,000 training rows rather than refitting on all labels. |
| 8 | Romina Mirshekar | 9 | **Approach:** Classical machine learning<br>**Methods:** Logistic regression using word/character TF-IDF over statements and metadata; comparison against statement-only word features.<br>**Validation:** Grouped holdout AUC: statement-only 0.8216; word/character features plus metadata 0.8557.<br>**Test AUC:** Test 0.87862 exceeds grouped holdout 0.8557; no clear overfitting signal, though one split limits certainty.<br>**+** Duplicate-aware grouping and training-only vectorization provide sensible leakage safeguards.<br>**+** Clear runtime comparison and appropriate distinction between pattern recognition and factual verification.<br>**−** Only two configurations and one split; character-feature and metadata gains are not isolated.<br>**−** Missing regularization and vectorizer settings reduce reproducibility; unseen-source robustness remains untested. |
| 9 | Martin Szugat Submission #1 | 10 | **Approach:** Classical machine learning<br>**Methods:** Custom TypeScript logistic regression with word TF-IDF, metadata tokens, and simple statement signals.<br>**Validation:** Holdout AUC: unigrams 0.7764; bigrams 0.7867; metadata/final 0.8619.<br>**Test AUC:** Test 0.87081 slightly exceeds validation 0.8619; broadly consistent, without an obvious overfitting signal.<br>**+** Explicit fold-local preprocessing and reproducible implementation details.<br>**+** Useful ablations, coefficient interpretation, and recognition of speaker-dependent generalization.<br>**−** Configuration selection reuses one holdout; no grouped or temporal evaluation.<br>**−** Near-label metadata such as 'sd:fake' warrants closer provenance scrutiny. |
| 10 | Simcha | 11 | **Approach:** Hybrid lexical and transformer ensemble<br>**Methods:** Word/character TF-IDF and mean-pooled frozen DistilBERT embeddings, separate logistic regressions, validation-tuned weighted averaging.<br>**Validation:** TF-IDF 0.81379; embeddings 0.82128; weighted ensemble 0.83310.<br>**Test AUC:** Test 0.86346 exceeds validation 0.83310; plausible split variation, but missing validation details prevent firm leakage conclusions.<br>**+** Component comparisons demonstrate complementary lexical and semantic signals.<br>**+** Reports the selected ensemble weights explicitly.<br>**−** Split construction, fold-local vectorization, and final refitting are unspecified.<br>**−** No uncertainty, contamination discussion, or analysis of generalization limitations. |
| 11 | Sü Suri | 7 | **Approach:** Classical machine learning<br>**Methods:** Metadata-enhanced logistic regression with regularization parameter search; feature engineering otherwise unspecified.<br>**Validation:** Stratified holdout AUC: best 0.8604 at C=0.5; statement baseline 0.8098; search 0.8420–0.8604.<br>**Test AUC:** Test 0.88153 exceeds validation 0.8604; no obvious overfitting gap, but undocumented preprocessing prevents leakage assessment.<br>**+** Clear regularization sweep and quantified improvement over the statement-only baseline.<br>**+** Explicitly reports full-training-data refitting for final predictions.<br>**−** Reads as an update rather than a standalone report: features, split size, and leakage controls are missing.<br>**−** No uncertainty, error analysis, or discussion of metadata shortcuts and validation-selection bias. |
