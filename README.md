# Skin Lesion Uncertainty Analysis

Experimental skin-lesion classification and predictive uncertainty analysis using Monte Carlo dropout.

## Contents

| File | Original filename |
|---|---|
| [notebooks/01_skin_lesion_mc_dropout.ipynb](notebooks/01_skin_lesion_mc_dropout.ipynb) | Cancer_Detection_Using_MC_dropout_method.ipynb |

## Run

For Python notebooks, install the inferred dependencies:

```bash
python -m pip install -r requirements.txt
python -m jupyterlab
```

Open a notebook and run cells from the beginning. Alternatively upload the notebook to Google Colab. Replace local or Google Drive paths with your own data locations before running. Notebooks are independent unless explicitly stated otherwise. For C++ files, compile and run each example separately with a compatible C++ compiler.

## Status and limitations

Requires the HAM10000 metadata CSV and image folders referenced in the notebook. Repeated function definitions and historical experiment cells remain unchanged. Check dataset partitions, patient/lesion leakage, calibration, and metrics before reporting results. This is an educational experiment, not a clinically validated diagnostic tool.

This collection was organised from existing files. Code-cell contents were preserved; saved outputs, execution counts, and transient notebook metadata were removed. The notebooks have not been executed as part of this preparation. Dependencies are inferred and unpinned, not a tested environment lockfile.

## Results

Run the examples to regenerate results. No accuracy, performance, or correctness claims are made here.

## Provenance

See [SOURCE_MAP.csv](SOURCE_MAP.csv) for the source archive and original filename. Preserve existing acknowledgements. No blanket open-source licence has been added because rights for adapted course material and datasets have not been established.
