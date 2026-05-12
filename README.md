
# Protein ΔG Classifier

A deep learning project for predicting protein stability (ΔG) classes from amino acid sequences using Facebook's ESM2 protein language model and TensorFlow.

## Overview

This repository contains a complete machine learning workflow for protein stability prediction:

1. **Data preprocessing** using protein language embeddings
2. **Model training** using TensorFlow/Keras
3. **Inference API** for predicting ΔG classes from new protein sequences

The project uses the PSPD (Protein Stability Prediction Dataset) and leverages transformer-based protein embeddings generated with Facebook's `ESM2 8M` model.

---

## Project Structure

```text
.
├── 01_data_preprocessing.ipynb   # Dataset loading, tokenization, and vectorization
├── 02_model_building.ipynb       # Model training and evaluation
├── 03_api.ipynb                  # Prediction API and inference workflow
├── DATA/                         # Saved NumPy arrays and trained assets
├── smallpspd.csv                 # Sample dataset (first 200k records)
├── requirements.txt              # Python dependencies
└── README.md
```

---

## Features

- Protein sequence preprocessing pipeline
- Protein embeddings using Facebook ESM2 transformer
- ΔG classification into 26 stability intervals
- TensorFlow/Keras dense neural network classifier
- Simple prediction API for inference
- Confusion matrix visualization
- Compatible with Google Colab

---

## Dataset

The project uses the **Protein Stability Prediction Dataset (PSPD)**:

- Source: Hugging Face PSPD dataset
- Dataset contains millions of protein sequences with associated ΔG values
- The notebooks use the first 200,000 samples (`smallpspd.csv`)

### Dataset Columns

Typical fields include:

- `aa_seq` — amino acid sequence
- `deltaG_bin` — discretized ΔG interval labels

### ΔG Classification

ΔG values are grouped into 26 integer-based intervals ranging approximately from:

```text
-10 Kcal/mol → +15 Kcal/mol
```

Each interval is encoded as a classification label.

---

## Model Architecture

The training notebook builds a TensorFlow neural network classifier using:

- Dense fully connected layers
- ReLU activation functions
- Softmax output layer
- Sparse categorical classification

### Embedding Model

The preprocessing stage uses:

- **Facebook ESM2 8M**
- Hugging Face Transformers API

Protein sequences are tokenized and converted into numerical embeddings before training.

---

## Installation

### Clone the Repository

```bash
git clone https://github.com/your-username/protein-deltaG-classifier.git
cd protein-deltaG-classifier
```

### Create Virtual Environment (Optional)

```bash
python -m venv venv

# Linux/macOS
source venv/bin/activate

# Windows
venv\Scripts\activate
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

---

## Dependencies

Main libraries used in this project:

- Python 3.9+
- TensorFlow
- NumPy
- Pandas
- Matplotlib
- Hugging Face Transformers

Example installation:

```bash
pip install tensorflow numpy pandas matplotlib transformers
```

---

## Workflow

## 1. Data Preprocessing

Run:

```bash
01_data_preprocessing.ipynb
```

This notebook:

- Loads the PSPD dataset
- Encodes ΔG labels
- Tokenizes protein sequences
- Generates ESM2 embeddings
- Saves NumPy arrays for training

### Output Files

Expected generated files:

```text
DATA/
├── X1.npy
├── X2.npy
├── X3.npy
├── X4.npy
└── y.npy
```

---

## 2. Model Training

Run:

```bash
02_model_building.ipynb
```

This notebook:

- Loads preprocessed embeddings
- Splits data into train/test sets
- Builds the TensorFlow classifier
- Trains the model
- Evaluates performance
- Generates confusion matrix visualizations

### Training Split

- 75% Training
- 25% Validation/Test

---

## 3. Prediction API

Run:

```bash
03_api.ipynb
```

The notebook exposes a simple prediction function:

```python
sequence_to_deltaG()
```

The function:

1. Accepts an amino acid sequence
2. Generates ESM2 embeddings
3. Loads the trained classifier
4. Predicts the ΔG class interval

---

## Example Usage

```python
sequence_to_deltaG()
```

Example input:

```text
MKTIIALSYIFCLVFADYKDDDDK
```

Example output:

```text
Predicted ΔG interval: 3 to 4 Kcal/mol
```

---

## Model Outputs

The classifier predicts ΔG interval labels rather than exact regression values.

Example intervals:

```text
-5 to -4
0 to 1
3 to 4
8 to 9
```

---

## Running in Google Colab

All notebooks include Colab badges and can be executed directly in Google Colab.

Recommended for GPU acceleration during embedding generation and training.

---

## Performance Visualization

The training notebook includes:

- Accuracy metrics
- Loss curves
- Confusion matrix plotting

These help evaluate classification quality across ΔG intervals.

---

## Troubleshooting

### Transformer Model Download Issues

If Hugging Face model downloads fail:

```bash
pip install --upgrade transformers huggingface_hub
```

---

### TensorFlow GPU Not Detected

Verify TensorFlow GPU support:

```python
import tensorflow as tf
print(tf.config.list_physical_devices('GPU'))
```

---

### Memory Errors During Embedding Generation

Protein embeddings may require large amounts of RAM/VRAM.

Possible solutions:

- Reduce batch size
- Use fewer samples
- Run on Google Colab GPU runtime

---

## Future Improvements

Potential enhancements:

- Switch from classification to regression
- Use larger ESM2 variants
- Hyperparameter optimization
- Add FastAPI deployment
- Docker support
- Sequence batch inference
- Model checkpointing

---

## License

Please add your preferred license information here.

Example:

```text
MIT License
```

---

## Acknowledgements

- Facebook AI Research (FAIR) for ESM2
- Hugging Face Transformers
- PSPD dataset contributors
- TensorFlow team

---

## Contributors

Add project contributors here.

Example:

```text
Amir Meshkini
```

---

## Citation

If you use this project in research or publications, please cite the associated repository or paper.

---

## Notes

This project is intended for educational and research purposes in bioinformatics and machine learning.
