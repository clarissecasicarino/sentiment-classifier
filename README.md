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

## III. Rationale for Chosen Dataset and Target Variable

This project uses a public dataset of COVID‑19–related tweets that contains tweet text plus basic metadata (such as user, timestamp, and location) collected during the early stages of the pandemic. This corpus is well suited to the problem because it captures real‑time public reactions to a major infectious disease, including a wide range of emotional and informational content, which makes it a good training ground for learning patterns of fear‑mongering, calm‑negative/concerned, and neutral/factual communication. The target variable in this project is a new 3‑class label that will be constructed on top of the tweet text, mapping each tweet into one of these tone categories rather than using standard sentiment labels like positive/negative/neutral.

### Source, Access Method, and Licensing/Ethical Considerations:

The dataset used in this project is the “COVID19 Tweets” collection hosted on Kaggle at:
https://www.kaggle.com/datasets/gpreda/covid19-tweets

The dataset is distributed under a **CC0 Public Domain license**. Even with a CC0 license, there are important ethical considerations. Tweets may still contain personal opinions, locations, or other attributes that could indirectly identify individuals, especially when combined with outside information. To mitigate this, the project focuses on aggregate modeling and analysis rather than individual users, avoids publishing handles or direct quotes tied to usernames, and paraphrases or anonymizes any example tweets included in reporting. The work also stays within a research/educational context and does not claim to provide an automated moderation tool ready for deployment.

### Summary of Key Features and Initial Concerns:

The dataset provides a set of structured fields describing each tweet. The most important features for this project include:

**1. Tweet text** (the main free‑text content), which is the primary input for classifying tweets as fear‑mongering, calm‑negative/concerned, or neutral/factual.

**2. Timestamp / date of posting**, which can be used to study how discourse changes over time and to ensure that only information available at posting time is used.

**3. Basic metadata** such as user location, language, and possibly engagement metrics (likes, retweets), which can be used for optional exploratory analysis or as auxiliary features (e.g., to see whether certain regions or time periods are more prone to fear‑mongering).

From the outset, there are several initial concerns:

**1. Class imbalance:** Because fear‑mongering is a specific, relatively extreme subtype of communication, there may be far fewer clearly fear‑mongering tweets than neutral or mildly negative ones, leading to skewed class distributions once the new 3‑class labels are created. This will need to be checked and potentially addressed with strategies like resampling, class‑weighted loss functions, or careful thresholding.

**2. Sampling and representation bias:** The dataset only reflects users who were active on Twitter and using COVID‑related terms during the collection period, which means it over‑represents certain demographics, languages, and regions while under‑representing others. As a result, the model may learn patterns specific to particular communities and may not fully generalize to all populations or to communication about future viruses.

**3. Temporal and topic drift:** The data comes from the COVID‑19 context, which had its own unique mix of fear, policy debates, and media narratives. When the model is later interpreted as a tool for future outbreaks (e.g., hantavirus‑related discourse), there is a risk that language patterns may shift, so any claims about generalization must be made cautiously and ideally validated on newer data.

## IV. Project Organization

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
