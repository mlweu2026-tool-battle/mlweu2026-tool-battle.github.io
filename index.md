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
| 7 | Nina | 0.88019 |
| 8 | Romina Mirshekar | 0.87862 |
| 9 | Martin Szugat Submission #1 | 0.87081 |
| 10 | Simcha | 0.86346 |

### Leaderboard 2: Analytical Quality (Report Review)

| Report Rank | User | AUC Rank | Comments |
|:--:|:--|:--:|:--|
| 1 | Timotej Giacomelli | 2 | **Approach:** Hybrid LLM, transformer, and classical ensemble<br>**Methods:** Opus-dominated rank blend with Sonnet, fine-tuned RoBERTa, MPNet, TF-IDF classifiers, LightGBM, and cross-fitted metadata rates.<br>**Validation:** Holdout AUC: Opus 0.9501; RoBERTa 0.8783; classical/transformer blend 0.8837; final 0.9557.<br>**Test AUC:** Test 0.95547 almost exactly matches validation 0.9557; excellent consistency, but shared public-data memorisation remains possible.<br>**+** Strong comparative experiments, blend sensitivity checks, and transparent separation of trained models from LLM contributions.<br>**+** Excellent hidden-test performance with explicit disclosure of memorisation risk and uncalibrated rank outputs.<br>**−** Public fact-check contamination is acknowledged but not experimentally tested.<br>**−** Many model and blend decisions reuse one holdout; exact LLM versions, prompts, and exemplar selection are underspecified. |
| 2 | Matthias Göbel | 3 | **Approach:** Hybrid lexical, metadata, and pretrained-embedding classifier<br>**Methods:** Single regularized logistic regression combining word/character TF-IDF, categorical metadata, and weighted frozen e5-small embeddings.<br>**Validation:** Five-fold OOF AUC 0.8731; baseline 0.8663; temporal 0.8915; speaker-grouped 0.8584.<br>**Test AUC:** Test 0.89830 exceeds OOF 0.8731; robustness checks support generalization, although selection and pretrained contamination remain unresolved.<br>**+** Exceptional ablations, harder validation splits, explicit corrections, and candid uncertainty analysis.<br>**+** Fold-local pipelines and cross-fitting support sound leakage reasoning; simpler final model is justified empirically.<br>**−** Extensive adaptive reuse of the same folds leaves selection optimism despite bootstrap intervals.<br>**−** Near-label subject tags and possible pretrained memorisation complicate claims of leakage-free factual detection. |
| 3 | Dean Abbott | 4 | **Approach:** Classical machine-learning ensemble<br>**Methods:** Bagged logistic regression and LightGBM; TF-IDF, SVD/NMF, metadata, cross-fitted target encodings, and neighbor label rates.<br>**Validation:** OOB-averaged AUC: logistic regression 0.8667; LightGBM 0.8596; final blend 0.8699.<br>**Test AUC:** Test 0.89555 exceeds OOB 0.8699; conservative bootstrap training sizes may contribute, but the difference exceeds reported resampling variation.<br>**+** Extensive paired experiments, subgroup analysis, and unusually clear separation of source signals from language understanding.<br>**+** Careful bootstrap duplicate handling and nested cross-fitting of supervised features.<br>**−** Transductive vocabulary and decompositions include evaluation inputs; validation is not strictly inductive.<br>**−** Repeated OOB-based selection lacks independent confirmation; uncertainty understates model-selection and population variability. |
| 4 | Martin Szugat Submission #2 | 1 | **Approach:** Hybrid zero-shot LLM and classical ensemble<br>**Methods:** Equal-weight probability blend of an unspecified zero-shot LLM and browser-based TF-IDF logistic regression with metadata.<br>**Validation:** Classical holdout 0.8798; 200-row subset: classical 0.8702, LLM 0.9739, blend 0.9726.<br>**Test AUC:** Best test AUC 0.96649 broadly matches subset blend 0.9726; small validation sample and possible LLM memorisation limit confidence.<br>**+** Highest hidden-test discrimination; same-row comparison identifies the LLM as the principal performance driver.<br>**+** Provides interpretable classical features and explicit preprocessing isolation.<br>**−** LLM identity, prompt, subset selection, and contamination checks are missing.<br>**−** Classical-only summary and conclusion contradict the submitted blend; track-record features lack construction details. |
| 5 | whistleblower | 5 | **Approach:** Hybrid lexical and frozen-transformer ensemble<br>**Methods:** TF-IDF logistic regression blended with Random Forest using cross-fitted BERT-head scores, style features, and smoothed source rates.<br>**Validation:** Five-fold mean AUC: logistic regression 0.8594±0.0090; BERT/forest 0.8567±0.0082; blend 0.8656±0.0088.<br>**Test AUC:** Test 0.89388 exceeds mean validation 0.8656; supports useful generalization, though the difference exceeds reported fold standard deviation.<br>**+** Nested group cross-fitting protects supervised intermediate features and keeps normalized duplicates together.<br>**+** Reports fold-level variability and consistent ensemble gains; removes train/test duplicate matches before final fitting.<br>**−** Exploratory selection still reuses outer folds without an untouched confirmation set.<br>**−** No speaker-disjoint or temporal tests; pretrained contamination and detailed component ablations remain unexamined. |
| 6 | Nina 2 | 6 | **Approach:** Classical machine-learning ensemble<br>**Methods:** Equal-weight logistic-regression ensemble combining metadata-as-text TF-IDF with statement TF-IDF and scaled categorical one-hot features.<br>**Validation:** Holdout AUC: text 0.81189; metadata variants 0.85397–0.86177; final ensemble 0.86462.<br>**Test AUC:** Test 0.89024 exceeds validation 0.86462 by 0.02562; favorable generalization, but the single holdout offers limited uncertainty assessment.<br>**+** Detailed pipeline specification and explicit exclusion of validation rows from preprocessing fits.<br>**+** Thoughtful distinction between dataset prediction, source reputation, and factual verification.<br>**−** Identical report to submission 2 does not explain their different test predictions.<br>**−** Reused random holdout and no full-data refit weaken evaluation and final training efficiency. |
| 7 | Nina | 7 | **Approach:** Classical machine-learning ensemble<br>**Methods:** Equal-weight logistic-regression ensemble combining metadata-as-text TF-IDF with statement TF-IDF and scaled categorical one-hot features.<br>**Validation:** Holdout AUC: text 0.81189; metadata variants 0.85397–0.86177; final ensemble 0.86462.<br>**Test AUC:** Test 0.88019 exceeds validation 0.86462 moderately; no obvious overfitting signal, though one split cannot establish leakage absence.<br>**+** Reproducible feature settings and explicit training-only preprocessing.<br>**+** Candid discussion of selection optimism, source shortcuts, and limits of factual interpretation.<br>**−** Multiple configurations selected on one random holdout; correlated claims remain uncontrolled.<br>**−** Final models use only 8,000 labeled rows, leaving available training information unused. |
| 8 | Romina Mirshekar | 8 | **Approach:** Classical machine learning<br>**Methods:** Regularized logistic regression using word/character TF-IDF over statements and metadata; normalized-statement-grouped holdout.<br>**Validation:** Grouped holdout AUC: statement-only 0.8216; word/character TF-IDF plus metadata 0.8557.<br>**Test AUC:** Test 0.87862 exceeds grouped validation 0.8557; compatible with split variation and refitting, not evidence of leakage.<br>**+** Duplicate-aware splitting and training-only vectorization strengthen evaluation integrity.<br>**+** Clear runtime comparison and appropriately cautious interpretation of source shortcuts.<br>**−** Only one grouped split; unseen-speaker and temporal robustness remain untested.<br>**−** Limited tuning details and no ablations separating character features from metadata gains. |
| 9 | Martin Szugat Submission #1 | 9 | **Approach:** Classical machine learning<br>**Methods:** Custom browser-based logistic regression with word TF-IDF, metadata tokens, and simple statement features.<br>**Validation:** Holdout AUC: unigrams 0.7764; bigrams 0.7867; metadata/final 0.8619.<br>**Test AUC:** Test 0.87081 slightly exceeds validation 0.8619; consistent performance, without evidence of substantial selection overfitting.<br>**+** Clear implementation details and explicitly fold-local preprocessing.<br>**+** Useful feature interpretation and recognition of unseen-speaker limitations.<br>**−** Single reused holdout; no duplicate-aware, speaker-disjoint, or temporal evaluation.<br>**−** Label-like metadata tokens warrant provenance scrutiny beyond the stated preprocessing controls. |
| 10 | Simcha | 10 | **Approach:** Hybrid lexical and transformer-embedding ensemble<br>**Methods:** Word/character TF-IDF and mean-pooled frozen DistilBERT embeddings; separate logistic regressions with validation-optimized probability blending.<br>**Validation:** AUC: TF-IDF 0.81379; embeddings 0.82128; ensemble 0.83310.<br>**Test AUC:** Test 0.86346 exceeds validation 0.83310; plausible sampling variation, but unspecified validation prevents reliable assessment of leakage or optimism.<br>**+** Clear component comparison demonstrates complementary lexical and embedding signals.<br>**+** Reports the selected ensemble weights explicitly.<br>**−** No split construction, sample counts, preprocessing isolation, or duplicate controls documented.<br>**−** Little reproducibility detail, error analysis, or discussion of limitations and weight-selection bias. |

