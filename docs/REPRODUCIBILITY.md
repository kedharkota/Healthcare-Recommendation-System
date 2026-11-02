# Reproducibility and visual sources

## Scope

This guide describes what is available in the committed project and what is required to reproduce it. The documentation update inspected source and saved outputs; it did not rerun model training or hardware/simulation experiments.

## Required inputs

The notebook expects `Training.csv`, `description.csv`, `diets.csv`, `medications.csv`, `precautions_df.csv`, `Symptom-severity.csv`, `symtoms_df.csv`, and `workout_df.csv`. These are not committed. The embedding matcher contains an empty `np.argmax()` call that must be completed before the text-input branch can run end to end.

## Entry point

Open `ML.ipynb` in Jupyter and review its installation and data-loading cells. The notebook mixes a Colab Drive mount with local Windows paths, so choose one environment and remove or skip cells that do not apply.

Provide the required CSVs, replace their paths, and install compatible versions of the imported libraries: pandas, NumPy, Matplotlib, scikit-learn, XGBoost, Transformers, sentence-transformers, fuzzywuzzy, python-Levenshtein, TextBlob, and pyspellchecker.

## Evidence and interpretation

The notebook includes classifier-evaluation code, but this README does not claim a verified benchmark. Model selection currently uses the test-set scores; reserve a separate final evaluation set before reporting generalization. The output is an experimental association with dataset labels, with no clinical diagnostic validation established.

## Visual provenance

All screenshots and experiment figures are tied to repository material. Workflow SVGs are explanatory illustrations. The full image inventory is in [assets/sources.json](assets/sources.json).

| Visual | Source |
| --- | --- |
| [overview.svg](assets/overview.svg) | New explanatory project-workflow diagram based on the committed source and documentation; not a screenshot or measured result. |

## Validation

```bash
python tools/check_docs.py
```

The standard-library checker validates README/docs local link destinations and SVG/PNG/JPEG headers. It makes no external requests and installs no project runtime dependencies. External web links, model accuracy, image semantics, and full application execution need separate review.

## Refresh notebook visuals

The exporter reads saved `image/png` outputs without executing notebook code:

```bash
python tools/export_notebook_images.py "ML.ipynb"
```

Review the exported images, remove any unsuitable or private content, choose the figures that explain the project, and update the README links and `docs/assets/sources.json`. It does not manufacture results when a notebook has no saved PNG output.

## Reproduction record

For a new experiment or demo, record the source commit, environment versions, data provenance and split, configuration, command/notebook order, and resulting artifacts. Only label a measurement as reproduced after completing that run. Keep credentials and restricted datasets outside version control.
