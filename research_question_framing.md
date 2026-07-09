# Research Question Framing

## Provisional Lane 
### Advanced Lane A2: Growth / Recovery / Momentum Prediction (Mentor-Gated)
This is a provisional lane selection. The final lane will be confirmed by the end of Week 4 after discussing data availability and validation requirements with the mentor.

## Research Question
```text
Can historical search, engagement, and content signals be used to predict which content pages are likely to experience a significant decline in organic search performance over a future time window?
```

The goal is to investigate whether a machine learning model can rank pages according to future decline risk more effectively than a transparent rule-based baseline. The project focuses on prioritizing pages for human review rather than automatically making SEO decisions.

## Motivation

Large websites often contain thousands of pages, making manual review impractical. SEO analysts need to decide which pages deserve attention first because reviewing every page is not feasible.

Observable signals such as search impressions, click-through rate (CTR), average ranking position, content freshness, engagement, and content age may contain useful information about future performance. Rather than relying only on manually designed thresholds, machine learning may identify combinations of signals that improve prioritization.

The objective is not to replace SEO analysts but to help them allocate their limited review time more efficiently.

## Unit of Analysis

The unit of analysis is **one content page at a specific prediction point**.

Each training example represents a page described by historical search, engagement, and content features collected before the prediction date.

## Decision Supported

The project supports the following decision:
```text
Which pages should an SEO analyst review first because they are most likely to experience future performance decline?
```
The output is a ranked list of pages ordered by predicted future decline risk.

## Possible Actions

After reviewing a recommended page, an SEO analyst may decide to:

- Refresh outdated content.
- Expand thin or incomplete content.
- Improve page titles or meta descriptions.
- Improve user engagement or content quality.
- Merge, prune, or consolidate overlapping content.
- Continue monitoring without making changes.

The model recommends pages for review only. The final SEO decision remains with the analyst.

## Proposed Features

Potential predictive features include:

- Content age
- Days since last update
- Search impressions
- Click-through rate (CTR)
- Average search position
- User engagement metrics
- Word count
- Content type
- Freshness indicators

Only information available before the prediction date will be used as model features.

## Proposed Target

The preferred target is a future outcome rather than a current status.

Example target:
```text
Predict whether a page experiences a meaningful decline in organic visibility during the next 30 days using information from the previous 90 days.
```

## Baseline

A transparent rule-based baseline will be created before training any machine learning model.

Possible baseline rules include combinations of:

- Old content
- Low CTR
- Declining visibility
- Weak engagement
- Poor average ranking position

The machine learning model will be evaluated against this baseline.

## Validation Plan

Because this is a future prediction task, validation should prevent information leakage.

The preferred validation strategy is:

- Client-holdout validation, where pages from the same client do not appear in both training and testing datasets.
- Time-aware validation, where historical observations are used to predict future outcomes.

Performance will be measured using metrics that reflect the ranking task, including:

- Precision@20
- Precision@50
- Average Precision
- ROC-AUC

## Cost of Incorrect Recommendations

A false positive may cause analysts to spend time reviewing pages that are unlikely to decline.

A false negative may cause genuinely at-risk pages to be missed, potentially resulting in continued loss of organic traffic before intervention.

Because analyst time is limited, ranking quality is more valuable than maximizing overall classification accuracy.

## Why This Is More Than "Training a Model"

The primary objective is not simply to maximize predictive performance.

The project requires:

- Defining a prediction problem that matches a real SEO decision.
- Selecting features that would be available at prediction time.
- Avoiding information leakage between feature and target windows.
- Comparing machine learning against a transparent baseline.
- Producing interpretable rankings that support human decision-making.
- Evaluating whether the model provides meaningful practical value for prioritizing SEO review.
