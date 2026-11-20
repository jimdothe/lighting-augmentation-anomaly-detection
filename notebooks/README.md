# Notebooks

Add the project's work as Jupyter notebooks:

1. Member 1 builds the Rice loader check and split/scene manifest.
2. Member 1 trains and validates the reference autoencoder.
3. Member 2 runs the stock EfficientAD pilot and all four settings through the same training code.
4. Member 3 demonstrates the lighting function on one tile for Member 2.
5. Member 4 evaluates the saved models and produces the final table and error figure.

Use reusable helpers from `src/`. Read the dataset root from `MVTEC_AD2_ROOT`.
Keep test data out of training notebooks, preserve official splits and record
the configuration and seed for every run. Notebooks have not been implemented
in this initial repository setup.
