# Team plan for the lighting experiment

DATA 255, Team 1, Fall 2026. Start with Rice. On November 25, use the pilot timing to decide whether to add Walnuts before full training.

Pick one role and replace its `[Name]` with your name. The file paths below tell you where to put the work as you build it. All six deadlines appear in the handoff table.

### Member 1

**Data, reference model and slides** · [Name]

1. **Start with Rice.** Follow the [data guide](../data/README.md). Build the loader in `src/`. Keep each image’s split, scene and lighting label. Give Member 2 a notebook that prints the training and validation counts and shows that one full image yields 80 edge-aligned tiles of 256 × 256 pixels.
2. **Supply the reference results.** Train a small convolutional autoencoder on normal Rice crops. Before Member 2 writes the progress report, send the pilot loss, seconds per step and one score for each of the 35 validation images. For the full run, give Member 2 the saved model locations, validation scores and reload instructions for seeds 11, 22 and 33 per selected category.
3. **Reproduce one result and make the slides.** Use Member 4’s command and checkpoint to rerun their Rice score. In `results/reproduction.md`, record the command, expected score, observed score and any difference. Give the note and presentation slides to Member 3.

### Member 2

**EfficientAD training and project code** · [Name]

1. **Start with stock EfficientAD-S.** Set up Anomalib, the pretrained teacher and Imagenette using the [source links](references.md). When the loader arrives, time a 1,000-step Rice pilot with S00. Put the loss, normal-validation scores and runtime from both baselines in the 2–3-page progress report. Validation contains only normal images, so use score summaries there and compute AUROC on the final labeled test set.
2. **Choose the scope and train.** Forecast 12 EfficientAD fits at 40,000 steps each and three reference fits at 10,000 steps each per category. Add Walnuts only if both categories fit 48 hours of training and 8 hours of evaluation. Record the choice. Use one pipeline for stock (S00), brightness (S10), contrast (S01) and both (S11), with Member 3’s function and seeds 11, 22 and 33. Member 1 supplies the reference fits.
3. **Hand the models to Member 4.** Create `results/run_log.csv` with one row per model, setting, category and seed. Include the checkpoint location, validation-score file and reload command. Verify Member 4 can open the files. Put the environment and run instructions in the README for the final code package. Confirm the Canvas upload.

### Member 3

**Lighting adjustments and final report** · [Name]

1. **Start with one RGB tile.** Create `src/lighting.py` using the [four settings](../configs/study.json). Before normalization, apply enabled adjustments together half the time. Draw each enabled factor independently from 0.8 to 1.2, apply brightness before contrast, and clip pixels to [0, 1]. S00 and evaluation return the original tile.
2. **Give Member 2 a working example.** Before the pilot report is assembled, send the function, a short example call and a labeled before/after tile. Check that S00 leaves the tile unchanged. Member 2 can run the stock pilot while you build this.
3. **Own the final report.** Draft the question, data and methods during training. Add Member 4’s verified table and error figure, Member 1’s reproduction note and each member’s short write-up. Deliver the reviewed 6–8-page report with the slides and runnable code.

### Member 4

**Evaluation and figures** · [Name]

1. **Start with the scoring notebook.** Try a clean image scored 0.1 and a defective image scored 0.9. The expected AUROC is 1.0. For real images, use the highest anomaly-map value across all tiles as the whole-image score.
2. **Evaluate the saved models.** Read Member 2’s run log. Set the alarm cutoff for each model, category and seed at the 95th percentile of its normal-validation image scores. Freeze the scoring rules, then evaluate the public test images. Compare S11 with S00 under changed and regular light. Keep all views of a scene together when estimating uncertainty. Follow the [proposal](proposal.pdf) for the ablations, secondary metrics and timing.
3. **Give each person what they need.** Give Member 3 `results/auroc.csv` with changed-light and regular-light AUROC by category, setting and seed, plus one error image with a heatmap and caption. For Member 1, mark one Rice table value and put its checkpoint, evaluation command and expected score in the README.

## Six team handoffs

| Due | Lead | What must be ready |
| --- | --- | --- |
| Nov 23 | Member 1 | Member 2 can run the Rice loader and see 313 training images, 35 validation images and 80 tiles per full image. |
| Nov 25 | Member 2 | The progress report includes both baseline pilots and the decision on Walnuts. Member 3’s lighting example is ready for integration. |
| Dec 3 | Member 2 | Member 4 can reload every model from the run log. Rice requires 15 total runs, or 30 with Walnuts. |
| Dec 5 | Member 4 | Member 3 has the AUROC table and illustrated error. Flag any regular-light drop over 0.02. Member 1 has one Rice result to reproduce. |
| Dec 7 | Member 1 | Member 3 has the reproduction note with the expected and observed Rice scores. |
| Dec 9 | Member 3 | The reviewed report, Member 1’s slides and Member 2’s runnable code are ready to submit. |

Each member gives Member 3 a short write-up, reviews another member’s work and presents their part. Member 2 confirms the Canvas upload by the official final report deadline of **December 16, 2026**.

[Get the data](../data/README.md) · [Experiment settings](../configs/study.json) · [Project on GitHub](https://github.com/jimdothe/lighting-augmentation-anomaly-detection)
