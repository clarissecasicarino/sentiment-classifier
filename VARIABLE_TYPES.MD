# VARIABLE_TYPES

## Columns and types

- `user_name` — **categorical_id**
  - String identifier of the user account. Very high cardinality; used only for deduplication / reference, not as a model feature.

- `user_location` — **categorical**
  - Free‑text user location. High‑cardinality, noisy; mainly for exploratory analysis.

- `user_description` — **text**
  - Free‑form user profile description. Optional text feature; not needed for the initial baseline model.

- `user_created` — **datetime**
  - Account creation timestamp. Can be transformed into account age (numerical) if used.

- `user_followers` — **numerical**
  - Count of followers for the user.

- `user_friends` — **numerical**
  - Count of accounts the user follows.

- `user_favourites` — **numerical**
  - Count of favourites/likes for the user.

- `user_verified` — **binary**
  - Whether the user is verified (True/False).

- `date` — **datetime**
  - Timestamp of the tweet. Can be decomposed into date/time features (day, month, etc.).

- `text` — **text**
  - Tweet content. This is the primary input feature for the classification task.

- `hashtags` — **text_set**
  - Hashtags used in the tweet (string containing one or more tags). Can be treated as text tokens or parsed into a set.

- `source` — **categorical**
  - Client/application used to post the tweet (e.g., Twitter for iPhone, web).

- `is_retweet` — **binary**
  - Indicates whether the tweet is a retweet (0/1). Can be used for filtering or as a simple feature.

## Target variable

- `tone_label` — **target (categorical, 3 classes)**
  - Planned label indicating whether the tweet is:
    - fear‑mongering
    - calm‑negative/concerned
    - neutral/factual
