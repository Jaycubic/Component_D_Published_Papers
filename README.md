# Component D — Published Papers Register

**CSIT332 · Principles of Machine Learning · Semester Project**
**Component D · Group 8**

## What this is

This repository contains the Component D literature register for a project studying how often published claims that one classifier "wins" are backed by enough data to be trustworthy. The register captures study sample size, the number of classifiers compared, the reported gap between the winner and runner-up, and whether a significance test was used.

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

### Week 1 source workbook

`Component D_Papers.xlsx` — the supplied Week 1 workbook, with three sheets:

| Sheet | Contents |
|---|---|
| **Paper** | One row per paper, 20 rows. Columns: `paper_id`, `citation`, `doi_or_url`, `sample_size`, `n_events`, `prevalence`, `n_classifiers`, `winner`, `winner_score`, `runner_up_score`, `protocol`, `test_reported`, `claim_in_abstract`, `notes` |
| **Rejection Tally** | Candidate papers that were screened but did not qualify, grouped by reason (preprint, full text inaccessible, review/meta-analysis rather than a primary study, no single declared winner, sample size too small or unclear), with the two most common reasons highlighted |
| **Notes on Difficult Fields** | A short account of which columns were genuinely hard to fill in consistently across papers, and the rule applied each time — e.g. what to do when a paper's *declared* winner doesn't match the numerically highest score in its own results table, or when reported prevalence describes data before a resampling step rather than what the models actually saw |

### Week 2 deliverables

- `Component_D_Week2_40_Paper_Register.xlsx` — the extended register with **40 paper rows** and 16 columns. It retains 18 Week 1 entries and adds 22 screened records. The original 14 Week 1 fields are preserved, with `n_classifiers_total` and `gap_metric` added. Supporting sheets include the cover and notes, rejection tally, coding decisions, and source links for the additions.
- `Component_D_Week2_10_Paper_Calibration.xlsx` — a separate coding file for the ten references assigned in `10Papers.docx`. Its coding sheet uses exactly the 14 Week 1 columns.

## A note on judgment calls

A few columns required a consistent rule rather than a single "correct" answer:

- **`winner` / `winner_score`** always reflects the paper's *own stated conclusion*, even on the handful of occasions where a different model scored marginally higher in the results table. The point of this register is to capture what was *claimed*, not to re-referee the paper.
- **`runner_up_score`** is left blank (never guessed) when it could not be recovered from accessible text — this is itself a data point worth tracking, not a gap to paper over.
- **`prevalence`** distinguishes cases where the value is genuinely unreported from cases where it describes pre-resampling data (e.g. before SMOTE) and so doesn't reflect what the models were actually trained and evaluated on.
- **Week 2 fields:** `n_classifiers_total` records the reported classifier count, including supplementary material when verified; counts that have not been independently checked against supplements are flagged in the workbook. `gap_metric` identifies the metric used for the winner/runner-up comparison. Runner-up values that could not be recovered are left blank rather than estimated.
- The Week 2 register flags source discrepancies and ambiguous coding decisions in its notes. In particular, it distinguishes a paper's declared winner from the numerically highest score when they differ.

## Status

The Week 1 source workbook contains 20 paper rows. Its supplied rejection tally says 7 accepted, which does not reconcile with those 20 rows; this discrepancy is recorded in the Week 2 workbook rather than silently reconciled. The Week 2 register contains 40 rows (18 retained Week 1 entries plus 22 additions). Two Week 1 entries were not carried forward: an arXiv preprint and a record whose traditional-model comparison used a separate cohort rather than a like-for-like comparison.

The contributor names were not present in the supplied source files and must be added to the workbook cover before submission. Group 7's independent coding was not supplied, so no inter-group agreement statistic is reported. Some runner-up scores and supplement classifier counts still require source-level verification; these are flagged in the register and should be checked before downstream analysis.
