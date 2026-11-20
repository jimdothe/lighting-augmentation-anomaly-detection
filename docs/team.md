# Team plan for the lighting experiment

DATA 255, Team 1, Fall 2026. Start with Rice. On November 25, use the pilot timing to decide whether to add Walnuts before full training.

## Choose one role

| Owner | What you do |
| --- | --- |
| Member 1 · [Name] | Build the image loader and train the reference autoencoder. Give the loader and saved models to Member 2. Later, independently reproduce one Rice score and prepare the slides. |
| Member 2 · [Name] | Train all four EfficientAD settings with the same code. Integrate Member 3’s lighting function, write the progress report, and give Member 4 the saved models, validation scores and reload commands. Confirm the final Canvas upload. |
| Member 3 · [Name] | Build the brightness-only, contrast-only and combined adjustments. Give Member 2 the function and one example for the pilot. Write the final report from Member 4’s results and Member 1’s reproduction note. |
| Member 4 · [Name] | Check the scoring code on a small example. Set alarm cutoffs using normal validation images, evaluate the saved models and explain the results with a table and an illustrated error. |

## Six team handoffs

| Due | Lead | What must be ready |
| --- | --- | --- |
| Nov 23 | Member 1 | Give Member 2 a Rice loader that reads 313 normal training images and 35 normal validation images. Check that a full image produces 80 tiles. |
| Nov 25 | Member 2 | Deliver the 2–3-page progress report with validation scores from the autoencoder and stock EfficientAD. Use pilot timing to record whether Walnuts fits the budget. |
| Dec 3 | Member 2 | Hand Member 4 the run log, saved models, reload commands and validation scores. Three seeds per setting give 15 runs for Rice or 30 with Walnuts. |
| Dec 5 | Member 4 | Give Member 3 the changed-light and regular-light AUROC table and one illustrated error. Flag any regular-light drop over 0.02. Give Member 1 a Rice score to reproduce. |
| Dec 7 | Member 1 | Rerun the Rice score from the README. Give Member 3 the command, expected score and observed score. |
| Dec 9 | Member 3 | Finish the reviewed 6–8-page report. Include Member 1’s slides and Member 2’s runnable code in the submission package. |

Each member gives Member 3 a short write-up, reviews another member’s work and presents their part. Member 2 confirms the Canvas upload by the official final report deadline of **December 16, 2026**.

[Get the data](../data/README.md) · [Experiment settings](../configs/study.json) · [Project on GitHub](https://github.com/jimdothe/lighting-augmentation-anomaly-detection)
