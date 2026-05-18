# Sentiment Classifier

## I. Problem Definition & Context

### Problem Statement:

Predict whether a public‑health‑related tweet (such as about COVID‑19 or future emerging viruses) will be fear‑mongering, calm‑negative/concerned, or neutral/factual within its posting time using data recorded up to that posting time so that we can distinguish between panic‑inducing messages and more constructive or informational discourse, helping platforms and users respond appropriately to new outbreaks without amplifying unnecessary fear.

### Hypothesis:

Public‑health‑related tweets that are fear‑mongering, calm‑negative/concerned, or neutral/factual exhibit systematically different linguistic and semantic patterns.

- `Fear‑mongering` tweets are expected to contain more emotionally charged and catastrophic language (e.g., “disaster”, “end of the world”), higher levels of certainty about worst‑case outcomes, and fewer explicit references to trusted sources or concrete evidence.
- `Calm‑negative/concerned` tweets are expected to express worry or frustration (e.g., about loved ones, restrictions, or case numbers) but with less extreme wording and sometimes with personal context or advice.
- `Neutral/factual tweets` are expected to contain more descriptive language (e.g., case counts, dates, locations), references to institutions or studies, and hedging or cautious wording, with relatively low emotional intensity.

Therefore, a text classification model trained on COVID‑era public‑health tweets should be able to learn these patterns and generalize them to future outbreaks, identifying which messages amplify panic and which contribute to informed, constructive discourse.

## II. Societal Relevance and Stakeholders

### Societal Relevance:

During outbreaks like COVID‑19 and future emerging viruses, social media becomes a main source of information and emotion, and fear‑mongering content can fuel anxiety, stigma, and poor decisions, while factual or calmly concerned messages support informed, collective action. This model helps distinguish panic‑inducing tweets from constructive or informational ones, enabling platforms to reduce the spread of sensational content, public‑health agencies to monitor and respond to public fear, and everyday users to stay informed about new health threats without being overwhelmed.

### Stakeholders and Decision Scenarios:

- **General public / individual users:** can benefit from indicators or tools that surface more balanced or calmly concerned content, helping them stay informed about new viruses without being overwhelmed by panic.

- **Social media platforms:** can use such a model as one signal in ranking or advisory systems—for example, deprioritizing clearly fear‑mongering tweets in recommendations or adding context labels—while still respecting free‑speech constraints.

- **Public‑health agencies and NGOs:** can track spikes in fear‑mongering vs factual discourse over time, identify emerging misconceptions early, and target communication campaigns to address specific fears.

- **Researchers and policymakers:** can study how fear and information spread in real time during outbreaks, informing guidelines for crisis communication and mental‑health support.

## III. Project Organization

```
├── LICENSE            <- Open-source license if one is chosen
├── Makefile           <- Makefile with convenience commands like `make data` or `make train`
├── README.md          <- The top-level README for developers using this project.
├── data
│   ├── external       <- Data from third party sources.
│   ├── interim        <- Intermediate data that has been transformed.
│   ├── processed      <- The final, canonical data sets for modeling.
│   └── raw            <- The original, immutable data dump.
│
├── docs               <- A default mkdocs project; see www.mkdocs.org for details
│
├── models             <- Trained and serialized models, model predictions, or model summaries
│
├── notebooks          <- Jupyter notebooks. Naming convention is a number (for ordering),
│                         the creator's initials, and a short `-` delimited description, e.g.
│                         `1.0-jqp-initial-data-exploration`.
│
├── pyproject.toml     <- Project configuration file with package metadata for
│                         sentiment_classifier and configuration for tools like black
│
├── references         <- Data dictionaries, manuals, and all other explanatory materials.
│
├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
│   └── figures        <- Generated graphics and figures to be used in reporting
│
├── requirements.txt   <- The requirements file for reproducing the analysis environment, e.g.
│                         generated with `pip freeze > requirements.txt`
│
├── setup.cfg          <- Configuration file for flake8
│
└── sentiment_classifier   <- Source code for use in this project.
    │
    ├── __init__.py             <- Makes sentiment_classifier a Python module
    │
    ├── config.py               <- Store useful variables and configuration
    │
    ├── dataset.py              <- Scripts to download or generate data
    │
    ├── features.py             <- Code to create features for modeling
    │
    ├── modeling
    │   ├── __init__.py
    │   ├── predict.py          <- Code to run model inference with trained models
    │   └── train.py            <- Code to train models
    │
    └── plots.py                <- Code to create visualizations
```

---
