# Effects of Lighting Augmentation on Industrial Anomaly Detection

DATA 255, Team 1, Fall 2026.

We will study whether additional brightness and contrast augmentation helps
EfficientAD detect defects under changed lighting while preserving performance
under regular lighting. We start with Rice from MVTec AD 2. On November 25,
Member 2 uses the pilot timing to decide whether to add Walnuts.

## Start with your role

| Your role | Your first task |
| --- | --- |
| [Member 1 — data, reference model and slides](docs/team.md#member-1) | Build the Rice loader and show Member 2 that one image yields 80 tiles. |
| [Member 2 — EfficientAD training and code](docs/team.md#member-2) | Set up stock EfficientAD-S for the Rice pilot while the loader is being built. |
| [Member 3 — lighting and final report](docs/team.md#member-3) | Write the lighting function and show Member 2 what it does to one tile. |
| [Member 4 — evaluation and figures](docs/team.md#member-4) | Build the scorer and check it on two example scores while the models are being trained. |

[See the six team deadlines and what must be ready at each one.](docs/team.md#six-team-handoffs)

## Current status

The group project is confirmed. This repository contains the proposal, planned
experiment settings, data access instructions and team responsibilities. Model
implementation and measured pilot results will be added next. Dependency
versions will be recorded after the pilot establishes a working environment.

The downloaded dataset is stored separately from this repository. Raw images,
model weights and local environment files are excluded from Git.

## Study

| Part | Planned approach |
| --- | --- |
| Reference baseline | Small convolutional autoencoder trained on normal images |
| Strong baseline | EfficientAD-S using Anomalib |
| Investigation | Extra brightness and contrast augmentation during training |
| Main comparison | Combined augmentation (S11) versus original EfficientAD (S00) |
| Ablations | Remove brightness (S01) or contrast (S10) from the combined setting |
| Seeds | 11, 22 and 33, paired across settings |
| Primary metric | Image AUROC pooled over changed lighting for Rice. If Walnuts is added, report each category and their equal-weight average. |

Preserve official splits. Use normal validation data for calibration and
thresholds, and freeze choices before final test evaluation. Keep lighting views
of each physical scene together when estimating uncertainty.

The full plan has 30 training runs across Rice and Walnuts. The Rice-only minimum
has 15. The proposed compute budget is an allocation, not a measured runtime;
the 1,000-step pilot will determine feasibility.

## Repository layout

- `docs/proposal.pdf`: proposal for team review and course submission.
- `docs/proposal.docx`: editable version of the same proposal.
- [Team plan](docs/team.md) with one owner per task and six dated handoffs.
- `docs/references.md`: dataset, paper, implementation and pretrained-model sources.
- `docs/assistance.md`: record of material AI assistance.
- `configs/study.json`: planned settings; training code does not consume it yet.
- `data/README.md`: download instructions and dataset location convention.
- `notebooks/`: future data, training and evaluation notebooks.
- `src/`: future reusable helpers for those notebooks.
- `results/`: small result summaries and figures after experiments run.

## Getting the data

For the Rice pilot, open **DATA 255 DL Group Project** in Google Drive and download `rice.zip`. The [full Hugging Face download](https://huggingface.co/datasets/yuxinjiang11/AnomVerse/resolve/47809f7e8f0ec9991cc03083aeeba82d83cd3abf/mvtec_ad_2.zip?download=true) also includes Walnuts.
Follow the [setup instructions](data/README.md). Copy `.env.example` to `.env` and set
`MVTEC_AD2_ROOT` to the extracted dataset root. To export it in a local shell:

```sh
set -a
source .env
set +a
```

Do not copy the dataset into a tracked directory or commit local `.env` files.

## Team workflow

Implement each component on a separate branch and review changes through pull
requests. Keep notebook output concise. Commit the run log and small summaries
in `results/`. Store checkpoints and full score files outside Git and record
where teammates can access them.

Every member contributes a short write-up, reviews another member’s work and
presents their part. Member 1 independently reproduces a Rice score for Member
3’s final report. The team package is due internally December 9. Member 2
confirms the Canvas upload by the official December 16 final report deadline.

## Data license and attribution

MVTec AD 2 is licensed under CC BY-NC-SA 4.0. Follow its attribution,
noncommercial and share-alike terms. The dataset is not distributed in this
repository. Credit reused software, pretrained models and auxiliary data under
their respective terms; see [docs/references.md](docs/references.md).
