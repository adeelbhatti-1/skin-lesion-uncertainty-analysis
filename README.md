# Skin Lesion Uncertainty Analysis

Experimental HAM10000 skin-lesion classification and predictive uncertainty analysis using a convolutional neural network with Monte Carlo dropout.

## Contents

| File | Description |
|---|---|
| [notebooks/01_skin_lesion_mc_dropout_kaggle.ipynb](notebooks/01_skin_lesion_mc_dropout_kaggle.ipynb) | Kaggle-backed HAM10000 training and MC Dropout evaluation workflow |

## Dataset

The notebook downloads the public [Skin Cancer MNIST: HAM10000 dataset](https://www.kaggle.com/datasets/kmader/skin-cancer-mnist-ham10000) with KaggleHub. It recursively discovers both image archives and validates every metadata image ID before preprocessing. A Google Drive mount and manually copied `HAM10000_images_part_1`, `HAM10000_images_part_2`, or `HAM10000_metadata.csv` files are not required.

The initial download needs several GB of free disk space. KaggleHub reuses its cache on later runs. Public downloads are attempted without credentials; if Kaggle requests authentication or consent, follow the [KaggleHub authentication instructions](https://github.com/Kaggle/kagglehub#authenticate). Keep API tokens in KaggleHub's supported credential storage or a Colab secret named `KAGGLE_API_TOKEN`, never in the notebook or repository.

## Run in Google Colab

1. Upload or open `notebooks/01_skin_lesion_mc_dropout_kaggle.ipynb` in Colab.
2. Select **Runtime → Change runtime type → GPU**.
3. Run the notebook from the first cell. It installs KaggleHub, downloads the dataset, preprocesses the images, trains the model, and performs 50-pass MC Dropout evaluation.

The notebook uses 224×224 RGB images and can consume substantial RAM and GPU memory. Reduce `batch_size` from 16 to 8 if the Colab runtime runs out of memory.

## Run locally

Use Python 3.10 or newer and install the notebook dependencies:

```bash
python -m venv .venv
python -m pip install -r requirements.txt
python -m jupyterlab
```

Open the notebook and run its cells in order. A CUDA-capable TensorFlow setup is recommended for training, although the notebook can run on CPU more slowly. The notebook's `%pip install kagglehub` cell is safe to rerun when the package is already installed.

## Status and limitations

The workflow keeps the source experiment's seven classes, 500 resampled images per class, 75/25 image-level split, CNN architecture, and 50 stochastic MC Dropout passes. Balancing with replacement occurs before the split, so duplicate images—and images from the same lesion—can appear in both training and test sets. Reported metrics are therefore not an independent estimate of clinical performance. A research evaluation should split by lesion before resampling only the training data.

This is an educational experiment, not a clinically validated diagnostic tool. Review dataset partitions, class balance, calibration, uncertainty measures, and clinical validity before interpreting or publishing results. The notebook has been structurally and syntactically checked, but the complete multi-gigabyte download and training run are not part of repository validation.

## Results

Run the notebook to regenerate accuracy, confusion-matrix, predictive-variance, entropy, and expected-calibration-error results. No fixed performance or correctness claims are made here.

## Provenance

See `SOURCE_MAP.csv` if it is present in your source archive for the original filename and provenance. Preserve existing acknowledgements. No blanket open-source licence has been added because rights for adapted course material and datasets have not been established.
