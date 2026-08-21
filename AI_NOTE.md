# AI Collaboration Note

## Did You Use AI?

Yes — Claude (via Claude Code) was used throughout this session, from
scoping the track down to writing the notebook.

## How You Used It

I had it start by analyzing the challenge folder and summarizing the
tracks and dataset, then chose Track A myself. Its first pass was a
dependency-free Python script; I decided against that and had it rebuild
the same analysis as a Jupyter notebook instead, since I wanted to work
through the logic manually rather than accept a finished script. It
scaffolded the notebook structure first (markdown sections and hints,
empty code cells), and only wrote the actual pandas after I asked for it
directly.

## One Prompt, Workflow, Or Moment That Helped

I'd proposed defining a "suspicious row" as one where `accepted_output`
and `flagged_for_review` were both high. Claude pushed back: those two
fields aren't opposites, so their co-occurring isn't actually a
contradiction — stricter review policy alone can produce that pattern.
It pointed me at the real signal instead: `median_confidence` moving
*opposite* to `user_rating`/flag-rate, which is a genuine contradiction
(the model getting more confident while humans push back more). That
reframing is what Section 5a in the notebook actually checks — without
it I would have flagged the wrong rows.

## One Thing You Verified Or Decided Yourself

I asked directly whether we should build an ML model instead of
thresholds, since that's a natural next step for a "detect suspicious
rows" problem. I decided against it myself after weighing it: ~40 rows
over 7 non-independent days isn't enough for a real train/test split, and
the rubric explicitly doesn't reward model complexity for its own sake.
I kept the rule-based checks and only noted ML as a "next steps" item for
when there's more history. I also had the notebook's Section 6 rewritten
from a Q&A format into direct statements after reading it back and
deciding the question framing read weaker than just answering plainly.
