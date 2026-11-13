# HCLS Foundation Models

An open dataset of foundation models in healthcare and life sciences (HCLS), maintained by [Pallav Sharda](https://pallavsharda.com). Explore it visually at **[pallavsharda.com/hcls-fm](https://pallavsharda.com/hcls-fm/)**. This repo holds the raw data behind that page.

## Contents

1. [The lens](#the-lens)
2. [What is in the repo](#what-is-in-the-repo)
3. [Columns in models.csv](#columns-in-modelscsv)
4. [Submit a model or a correction](#submit-a-model-or-a-correction)
5. [Credits](#credits)
6. [License and citation](#license-and-citation)

## The lens

This is one person's research, applied with a consistent rubric (see [METHODOLOGY.md](METHODOLOGY.md)). It is not a census of every model released.
1. **Inclusion.** A model is listed if it passes three gates: is it a foundation model? -> is it trained on healthcare or life-sciences data? -> and does it fit one of the categories below.
2. **Prominence.** A listed model is marked `prominent` if it clears a published bar built on four criteria: 1. GitHub stars, 2. Hugging Face downloads, 3. citations, and 4. track record of the lab behind it. Everything else that passes the gates is marked as `tracked`.

All rules are in [METHODOLOGY.md](METHODOLOGY.md). As of November 2026, out of 165 total active models, 60 are prominent. Only about a third clear the adoption bar.

## What is in the repo

| Path | What it is |
| --- | --- |
| `models.csv` | One row per model. The source of truth for which models are listed. |
| `models/<area>/<slug>.md` | A short description of each model, plus dated notes (merges, renames). |
| `categories/<area>/` | A short narrative for each area and category. |
| `METHODOLOGY.md` | Inclusion gates and the prominence rubric. |

Areas and categories:
1. **Biology**: genomics, transcriptomics, protein, epigenomics, antibodies and biologics, multi-omics
2. **Chemistry**: small molecule
3. **Clinical**: medical imaging, digital pathology, clinical language and patient, surgical video
4. **Emerging**: cross-cutting work without a category-defining model yet

Load it in one line:
```python
import pandas as pd
df = pd.read_csv("https://raw.githubusercontent.com/pallavsharda/hcls-foundation-models/main/models.csv")
```

## Columns in models.csv

| Column | Meaning |
| --- | --- |
| `slug` | Unique, permanent ID. Matches the file name in `models/`. |
| `name` | Model name as commonly cited. |
| `org` | Lab, university or company behind it. |
| `area`, `category` | Where it sits in the taxonomy above. |
| `modality` | Input data: DNA, RNA, protein, SMILES, WSI, EHR text, imaging, video and so on. |
| `url` | Authoritative source: paper, model card, lab or vendor page. |
| `prominence` | `prominent` or `tracked`. See METHODOLOGY.md. |
| `interp_partner` | A published interpretability partnership, if any. |
| `tags` | Pipe-separated labels, for example `generative`, `multimodal`, `private` (weights not freely downloadable). |
| `params` | Parameter count where known. |
| `active` | `no` means the model was merged into a successor or retired. Kept for history. |
| `last_verified` | Date the row was last checked. |
| `source` | How the model entered the list. |
| `release_year` | Year the version named in the row first became public. |
| `first_release_year` | Year the first version of that model line became public. |

Blank means unknown or not applicable. One row covers one model line within one category, so newer versions replace older ones (for example Evo to Evo 2).

## Submit a model or a correction

Open an issue with the **[Submit a model](https://github.com/pallavsharda/hcls-foundation-models/issues/new/choose)** form. Every submission is checked by hand against the gates before it is added. This repo is published from a private working copy, so pull requests can't be merged directly; an issue is the way in.

## Credits

The list started from my own taxonomy of the field. Candidates were then drawn from five community lists, four surveys and the Hugging Face Hub:
1. [Awesome-Healthcare-Foundation-Models](https://github.com/Jianing-Qiu/Awesome-Healthcare-Foundation-Models) (Jianing Qiu and others)
2. [Awesome-Foundation-Models-for-Advancing-Healthcare](https://github.com/YutingHe-list/Awesome-Foundation-Models-for-Advancing-Healthcare) (Yuting He and others)
3. [Awesome-Bio-Foundation-Models](https://github.com/apeterswu/Awesome-Bio-Foundation-Models) (apeterswu)
4. [Awesome-Foundation-Models-in-Medical-Imaging](https://github.com/xmindflow/Awesome-Foundation-Models-in-Medical-Imaging) (xmindflow)
5. [Awesome-Medical-Large-Language-Models](https://github.com/burglarhobbit/Awesome-Medical-Large-Language-Models) (burglarhobbit)
6. [Foundation Model for Advancing Healthcare](https://arxiv.org/abs/2404.03264) (He et al.)
7. [A Comprehensive Survey of Foundation Models in Medicine](https://arxiv.org/abs/2406.10729)
8. [Biomedical Foundation Model: A Survey](https://arxiv.org/abs/2503.02104)
9. [Foundation Models in Biomedical Imaging: Turning Hype into Reality](https://arxiv.org/abs/2512.15808)
10. [Hugging Face Hub](https://huggingface.co/models), scanned monthly for new releases

Model names, organizations and links are facts belonging to their creators.

## License and citation
The data and text are licensed under [CC BY 4.0](LICENSE). Reuse is welcome with credit:
> Sharda, P. *HCLS Foundation Models*. https://github.com/pallavsharda/hcls-foundation-models
