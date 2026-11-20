# Dataset access

Use MVTec AD 2. Start with Rice. Add Walnuts only if the November 25 pilot timing fits the team’s budget.

## Choose one download

| What you need | Where to get it |
| --- | --- |
| Rice for the pilot | In Google Drive, open **Shared drives → DATA 255 DL Group Project** with your team account and download `rice.zip` (6.3 GB in Drive). The team’s Word and PDF plan also links directly to this folder. |
| The full dataset, including Rice and Walnuts | [Download the pinned ZIP from Hugging Face](https://huggingface.co/datasets/yuxinjiang11/AnomVerse/resolve/47809f7e8f0ec9991cc03083aeeba82d83cd3abf/mvtec_ad_2.zip?download=true) (38.2 GB). |

The [MVTec dataset page](https://www.mvtec.com/research-teaching/datasets/mvtec-ad-2) provides the paper, license and evaluation server information. [Anomagic](https://github.com/yuxin-jiang/Anomagic) lists the [Hugging Face mirror](https://huggingface.co/datasets/yuxinjiang11/AnomVerse/tree/47809f7e8f0ec9991cc03083aeeba82d83cd3abf) used for the project.

Keep the original category folders and license/readme. The study excludes
generated prompts, extra crops, annotated overlays and added mirror metadata.
Preserve official training, validation and test partitions.

## Location

Unzip your download and set `MVTEC_AD2_ROOT` in your local `.env` to the folder that directly contains `rice/`. For the Hugging Face ZIP, that folder is `mvtec_ad_2/`. The `walnuts/` folder is only needed if the team adds Walnuts.

```text
<MVTEC_AD2_ROOT>/
  rice/
    train/good/
    validation/good/
    test_public/good/
    test_public/bad/
    test_public/ground_truth/
  walnuts/
    train/good/
    validation/good/
    test_public/good/
    test_public/bad/
    test_public/ground_truth/
```

The data can stay outside this repository. Its `data/` directory is ignored
except for this README.

## Planned study subset

| Category | Training normal | Validation normal | Public test normal | Public test anomalous | Public masks |
| --- | ---: | ---: | ---: | ---: | ---: |
| Rice | 313 | 35 | 42 | 90 | 90 |
| Walnuts | 432 | 48 | 60 | 90 | 90 |
| Total | 745 | 83 | 102 | 180 | 180 |

The images are 2448 by 2048 RGB. Public test data has 282 images representing
47 physical scenes captured under six lighting conditions. Group views of the
same scene in uncertainty estimates.

Private test images are available without private ground-truth labels. Private
labels remain on the [official evaluation server](https://benchmark.mvtec.com/).
Private-server evaluation is a stretch goal, not part of the required comparison.

The original local download passed inventory and integrity checks on October 25,
2026. Counts match the published dataset specification. No official source-archive
checksum was available, so these checks do not certify byte identity to the
original MVTec archive or inclusion of later corrections.

Dataset copyright belongs to MVTec Software GmbH. Its license is **CC BY-NC-SA
4.0**; retain the original attribution and applicable terms.
