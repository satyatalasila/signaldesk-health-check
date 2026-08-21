# About This Project

SignalDesk is a fictional internal tool that a product team uses to run
AI-assisted workflows for other teams — summarizing sales leads, drafting
support replies, and clustering user feedback. The team shipped a new
prompt version partway through a week and wants to know, in plain terms:
what's actually working, what looks suspicious in the usage data, and
what they should check before rolling anything out further.

This project is a Jupyter notebook (`analysis.ipynb`) that answers that
question from one week of usage logs. It isn't a dashboard or a general
analytics tool — it's scoped to one read of one dataset, built to be
skimmed by a teammate in a few minutes rather than explored.

**What it does, in order:**
1. Loads the raw export and looks at it before touching anything.
2. Cleans what's safely fixable (casing, inconsistent missing-value
   formats) and separately flags a duplicate row rather than silently
   dropping it unnoticed.
3. Compares the three workflows using rate metrics — acceptance rate,
   minutes saved, and rating — instead of raw counts, so volume
   differences don't distort the comparison.
4. Checks whether the new prompt version helped, hurt, or is genuinely
   unclear, workflow by workflow.
5. Flags two distinct kinds of suspicious rows: model confidence
   trending against real user outcomes, and traffic volume that doesn't
   look like normal usage.
6. Closes with a plain-language findings section a non-technical
   teammate could read on its own.

See `README.md` for the track, assumptions, and data source, and
`AI_NOTE.md` for how AI was used while building this.
