# Submission README

## Track Chosen

Track A: Fictional Domain Packet (SignalDesk).

## What I Built

`analysis.ipynb` — cleans the messy usage export, compares the three
workflows on rate metrics (acceptance rate, avg minutes saved, rating),
checks before vs. after the Aug 4 prompt change, and flags two kinds of
suspicious rows: confidence trending against rating/review flags, and
volume spikes/duplicates. Outputs are saved in the notebook, readable
without rerunning it.

## Who It Is For

The product teammate who asked "what's working, what looks suspicious,
what should we look at next" — someone who wants a fast, honest read,
not a dashboard.

## Data Or Source Used

`data/product_usage_events.csv` (copied from this challenge's
`sample-data/`), 41 rows of fictional daily workflow usage.

## Assumptions I Made

- Prompt-change date is 2026-08-04, taken from the `notes` column.
- Exact-duplicate rows are export artifacts, so one copy is dropped.
- "Useful" = acceptance rate + minutes saved + rating together.
  "Suspicious" = confidence moving opposite to rating/flag rate.
- No ML model: ~40 rows over 7 days is too little for a real
  train/test split — a model would just memorize the week.

## Data Issues Or Caveats I Noticed

Inconsistent team casing, one exact duplicate row, `median_confidence`
blank in some rows and the literal string `"n/a"` in another, and two
confounded events close together for Support (new prompt on 08-04, a
review-policy change on 08-07) that make before/after unreliable there.
Full detail is in `analysis.ipynb`, Sections 2 and 6.

## What I Would Do Next With More Time

Pull in more days to check if the 08-07 Support drop is a blip or a trend,
make the spike threshold variance-aware instead of a fixed 2x-median, and
revisit "no ML" once there's enough history for a real train/test split.
