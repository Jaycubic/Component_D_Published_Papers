# Component D — Published Papers Register

**CSIT332 · Principles of Machine Learning · Semester Project**
**Week 1 Deliverable**

## What this is

This repository contains a register of **20 published, peer-reviewed papers** that each compare two or more machine learning classifiers on tabular data and declare one of them the winner. It is the raw material for a larger project studying how often such "our model wins" claims are backed by enough data to be trustworthy — this register captures what real published studies actually had (sample size, number of classifiers compared, reported gap between winner and runner-up, whether a significance test was used) so that question can be answered empirically rather than assumed.

## Inclusion criteria

A paper only made it into the register if **all** of the following held:

1. **Applied study** — uses ML to answer a question in some field (clinical, educational, financial, etc.). Papers proposing a new algorithm were excluded.
2. **Tabular data** — no images, text, or signal data.
3. **Two or more classifiers compared** on the same dataset.
4. **One model explicitly named as best** by the authors.
5. **Sample size reported** somewhere in the paper.
6. **Published in English, 2019 or later**, in a peer-reviewed venue (preprints were excluded even when otherwise strong candidates).

Papers were found via targeted searches (PubMed and related sources) using combinations of machine-learning, prediction, and comparison terms ("outperformed," "best performing," "highest AUC").

## File contents

`Component_D_Papers.xlsx` — three sheets:

| Sheet | Contents |
|---|---|
| **Paper** | One row per paper, 20 rows. Columns: `paper_id`, `citation`, `doi_or_url`, `sample_size`, `n_events`, `prevalence`, `n_classifiers`, `winner`, `winner_score`, `runner_up_score`, `protocol`, `test_reported`, `claim_in_abstract`, `notes` |
| **Rejection Tally** | Candidate papers that were screened but did not qualify, grouped by reason (preprint, full text inaccessible, review/meta-analysis rather than a primary study, no single declared winner, sample size too small or unclear), with the two most common reasons highlighted |
| **Notes on Difficult Fields** | A short account of which columns were genuinely hard to fill in consistently across papers, and the rule applied each time — e.g. what to do when a paper's *declared* winner doesn't match the numerically highest score in its own results table, or when reported prevalence describes data before a resampling step rather than what the models actually saw |

## A note on judgment calls

A few columns required a consistent rule rather than a single "correct" answer:

- **`winner` / `winner_score`** always reflects the paper's *own stated conclusion*, even on the handful of occasions where a different model scored marginally higher in the results table. The point of this register is to capture what was *claimed*, not to re-referee the paper.
- **`runner_up_score`** is left blank (never guessed) when it could not be recovered from accessible text — this is itself a data point worth tracking, not a gap to paper over.
- **`prevalence`** distinguishes cases where the value is genuinely unreported from cases where it describes pre-resampling data (e.g. before SMOTE) and so doesn't reflect what the models were actually trained and evaluated on.

## Status

20 of the eventual ~20-paper target collected. Two rows are reserved at the end of the Paper sheet for papers still pending intake.
