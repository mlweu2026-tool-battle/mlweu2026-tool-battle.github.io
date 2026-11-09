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

<!-- MOCK LEADERBOARDS START: delete everything down to MOCK LEADERBOARDS END before publishing real results -->

> **Mock data for layout testing only.** All participants, scores and comments below are fictional and do not reflect real results or the real performance of any method.

### Leaderboard 1: Predictive Performance (ROC-AUC)

| AUC Rank | User | AUC |
|:--:|:--|--:|
| 1 | user 3 gpu | 0.96703 |
| 2 | Volodymyr Havryliak | 0.89667 |
| 3 | user 2 tr | 0.89239 |
| 4 | Золочівська А. | 0.88240 |
| 5 | user 1 tifidf | 0.85113 |
| 6 | Demian Pavlyshenko | 0.79009 |
| 7 | Test1 | 0.50000 |

### Leaderboard 2: Analytical Quality (Report Review)

Report scores range from 0 to 100. In the comments, **+** marks a strength and **−** marks a weakness.

| Report Rank | User | AUC Rank | Comments |
|:--:|:--|:--:|:--|
| 1 | Volodymyr Havryliak | 2 | **Approach:** Hybrid transformer and classical stacked ensemble<br>**Methods:** Late-fusion DeBERTa, DistilBERT, TF-IDF linear models, metadata boosting; temporal target encoding and logistic-regression stacking.<br>**Validation:** Five-fold best-single OOF AUC 0.8749; stack diagnostic 0.8781; predicted test range 0.873–0.878.<br>**Test AUC:** Test 0.89667 exceeds diagnostic 0.8781 and predicted range; no observed overfitting gap, but claimed bounds are unjustified.<br>**+** Detailed architecture, fold handling, model comparisons, and stacking diagnostics; second-best hidden-test discrimination.<br>**+** Thoughtful temporal encoding and shuffled-label controls, with explicit acknowledgement of stacking optimism.<br>**−** Reused base OOF predictions require nested validation for an unbiased stack estimate.<br>**−** Shuffle results omit transformer learners despite full-pipeline claims; chance performance cannot certify complete leakage absence. |
| 2 | user 2 tr | 3 | **Approach:** Fine-tuned transformer ensemble<br>**Methods:** DeBERTa-v3-small and DistilBERT on text plus metadata; averaged probabilities and validation-selected checkpoints.<br>**Validation:** Stratified holdout AUC: DeBERTa 0.86972; DistilBERT 0.86510; ensemble not evaluated.<br>**Test AUC:** Ensemble test 0.89239 exceeds individual validation scores; ensemble gains or sampling variation plausible, without direct ensemble validation.<br>**+** Strong hidden-test discrimination using complementary pretrained encoders.<br>**+** Clear training configuration, stratification, checkpoint selection, and numerical-stability adaptations.<br>**−** Final ensemble was not validated, leaving its incremental benefit unmeasured.<br>**−** Small single holdout and checkpoint reuse limit confidence; contamination and duplicate overlap are unexamined. |
| 3 | user 3 gpu | 1 | **Approach:** Zero-shot LLM classification<br>**Methods:** Reported GPT API model gpt-6.1-sol judges statements and metadata using internal knowledge; outputs fake probabilities.<br>**Validation:** No independent validation; reports labelled-test ROC-AUC 0.96529.<br>**Test AUC:** Organiser test 0.96703 matches claimed test 0.96529; absent independent validation, contamination or test-label access remains unresolved.<br>**+** Best hidden-test discrimination among submissions.<br>**+** Explicitly acknowledges memorisation risk and contradictory probability instructions.<br>**−** Labelled-test evaluation is unexplained despite supposedly hidden labels, undermining evaluation independence.<br>**−** Conflicting real/fake instructions undermine interpretability; exact prompt and API configuration are missing. |
| 4 | Золочівська А. | 4 | **Approach:** Classical machine learning<br>**Methods:** Word unigram/bigram and character 3–5-gram TF-IDF; L2 logistic regression with selected metadata.<br>**Validation:** Stratified 80/20 holdout: ROC-AUC 0.8560; accuracy 0.7700.<br>**Test AUC:** Test 0.8824 exceeds validation 0.8560; compatible with sampling variation and full-data refitting, not evidence of leakage.<br>**+** Explicit partition-local feature fitting, target exclusion, and probability-output controls.<br>**+** Clear, reproducible pipeline with sensible complementary lexical representations.<br>**−** Single holdout provides no uncertainty estimate or speaker/duplicate robustness assessment.<br>**−** No ablations establish character-feature benefits or justify metadata exclusions. |
| 5 | user 1 tifidf | 5 | **Approach:** Classical machine learning<br>**Methods:** Concatenated statements and metadata; word unigram-to-trigram TF-IDF with LightGBM.<br>**Validation:** Single 85/15 random holdout ROC-AUC: 0.85157.<br>**Test AUC:** Test 0.85113 closely matches validation 0.85157; no evident generalization gap, though leakage cannot be excluded.<br>**+** Training-only vectorizer fitting explicitly prevents preprocessing leakage.<br>**+** Concise, reproducible settings and fast baseline suitable for the time limit.<br>**−** Single split lacks stated stratification, uncertainty estimates, and duplicate checks.<br>**−** Metadata contribution is asserted without an ablation or error analysis. |
| 6 | Demian Pavlyshenko | 6 | **Approach:** Classical machine learning<br>**Methods:** Field-specific TF-IDF and metadata; logistic regression selected over LightGBM.<br>**Validation:** Five-fold AUC: final 0.858 ± 0.008; text-only 0.812; LightGBM 0.840; final accuracy 0.774.<br>**Test AUC:** Test 0.7901 versus CV 0.858; substantial optimism, distribution shift, or thresholded submission scores warrant investigation.<br>**+** Thorough exploration identifies source priors, temporal drift, duplicates, and speaker overlap.<br>**+** Clear baselines, model comparisons, fold variability, and limitations.<br>**−** Random cross-validation does not isolate duplicate statements or unseen speakers.<br>**−** Reported thresholded final predictions would discard probability ranking information. |
| 7 | Test1 | 7 | **Approach:** Unidentifiable<br>**Methods:** No identifiable models or features<br>**Validation:** not reported<br>**Test AUC:** Test AUC 0.5000 indicates chance discrimination; no validation comparison possible.<br>**−** Meaningless report provides no methodological or reproducibility information. |


<!-- MOCK LEADERBOARDS END -->
