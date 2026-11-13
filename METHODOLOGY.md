# Methodology

Rubric version 2.0, revised 2026-11-13. A plain-language version lives at [pallavsharda.com/hcls-fm/prominence](https://pallavsharda.com/hcls-fm/prominence).

## Contents

1. [Inclusion gates](#inclusion-gates)
2. [Prominence rubric](#prominence-rubric)
3. [Prominent means clears the bar](#prominent-means-clears-the-bar)
4. [One row per model line](#one-row-per-model-line)
5. [How models are found and kept current](#how-models-are-found-and-kept-current)
6. [Known limits](#known-limits)

## Inclusion gates

A model is listed only if it passes all three:
1. **It is a foundation model.** Pretrained as a general-purpose substrate for many tasks, not a single-task classifier.
2. **It works on healthcare or life-sciences data.** DNA, RNA, protein, small molecules, pathology slides, EHR text, medical imaging, surgical or endoscopy video, and related modalities.
3. **It fits a category.** One of the categories in the README, or Emerging if it is cross-cutting.

Closed, gated and vendor-only models are listed when they pass, and carry the `private` tag.

## Prominence rubric

Four signals, each scored 0 to 2. N/A signals are left out rather than scored 0.

| Signal | 2 points | 1 point | 0 points | N/A when |
| --- | --- | --- | --- | --- |
| GitHub stars | 1,000 or more | 200 to 999 | under 200 | no public repo |
| Hugging Face downloads (last 30 days) | 10,000 or more | 1,000 to 9,999 | under 1,000 | not on Hugging Face |
| Citations of the primary paper | 1,000 or more | 200 to 999 | under 200 | no paper |
| Organization | see below | see below | see below | never |

Stars, downloads and citations are the **usage signals**. Organization is **provenance**.

### Counting rules

1. Downloads sum the official organization's repos for the model, across sizes and variants. Third-party mirrors, quantizations and fine-tunes don't count.
2. Citations use the paper for the version in the row. If that version has no paper yet, the founding paper of the model line is used.
3. Citation counts come from Semantic Scholar or OpenAlex.

### Organization

1. **2 points**: a major industry lab with a prior model in the list or independent citations of this one; an established biotech with a research track record; or a top academic lab with a foundation-model track record.
2. **1 point**: a recognized lab that doesn't meet the 2-point bar. A 2-point lab also drops to 1 when this model has under 100 citations and under 100 stars.
3. **0 points**: no identifiable lab or track record.

### Composite

`composite = organization + the two strongest usage signals + activity` (maximum 7)

Only the two strongest usage signals count. Models are adopted through different channels (code, weights, papers), and a channel nobody uses is not evidence against a model, so it neither adds nor subtracts.

**Activity (+1)**: commits, a new release, or continued announcements in the last 6 months. There is no penalty for inactivity, because a settled model can still be heavily used.

### Bands

| Band | Rule |
| --- | --- |
| High | composite 5 or more, with data on at least 2 usage signals |
| Medium | composite 4, or composite 5 or more with data on fewer than 2 usage signals |
| Low | composite under 4 |

The two-signal floor stops a single big number, such as a download count with no paper behind it, from carrying a model to high on its own.

### Two adjustments

1. **Recency.** If a model was released in the last 12 months, its organization scores 2, and it already shows traction (100+ citations, 200+ stars or 1,000+ downloads), it moves up one band, up to high. New releases haven't had time to collect stars and citations.
2. **Clinical deployment.** Many clinical models have no public repo and no Hugging Face page. For a clinical model where both are N/A, documented use with real patients or clinicians at a named health system counts as one usage signal worth 2 points. Pilots and prospective studies count; research-only licenses and vendor partnerships do not. Med-PaLM 2 (Mayo Clinic and HCA pilots) and AMIE (prospective study at Beth Israel Deaconess) qualify.

## Prominent means clears the bar

A model is `prominent` if and only if it scores high. The rule is applied both ways: on every re-score, tracked models that reach high are promoted and prominent models that fall below it are demoted. Any exception needs a written reason in the model's notes file.

## One row per model line

Successive versions of the same model family in the same category are one row. When a new version ships, it replaces the old one in place, and the model's notes file records the change. Old versions are discarded. The goal is to track the diversity of models, not each iteration. A sibling model in a different category or modality does get its own row. `first_release_year` keeps the year the model line started, so the timeline of effort stays visible.

## How models are found and kept current

New models are found by a monthly scan of Hugging Face, arXiv, bioRxiv, GitHub and lab announcements, plus outside submissions. Every addition, version change and prominence call is reviewed by hand before it lands. `last_verified` on each row records when it was last checked.

## Known limits

1. Thresholds are judgment calls. They were set to separate broad adoption from niche use in this field, not derived statistically.
2. Stars, downloads and citations measure the research community. They undercount use inside companies and hospitals, which is why the clinical-deployment adjustment exists.
3. Organization scoring rewards track record, so a strong first model from an unknown team has to earn its place on usage alone.
4. Counts are snapshots taken at scoring time and drift between re-scores.
