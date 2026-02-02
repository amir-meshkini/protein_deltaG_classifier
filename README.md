# protein_deltaG_classifier
A project to estimate the change in Gibbs free energy caused by denaturalizing process of a given amino acid sequence. 

## How does it work
* In this Project the first 200000 records of the [PSPD dataset](https://huggingface.co/datasets/benchang323/protein-stability-prediction) ([licensed by MIT](https://choosealicense.com/licenses/mit/)) are tokenized and vectorized, using the Facebook's `EMS2 8M` PLP (Protein Language Processing) model. (Notebook number 1)

* The vectorized data is then used as the training data for our ΔG classifier prediction model. (Notebook number 2)

## How to use 
1. Clone the repository and install the required packages in a virtual environment; or open in colab via provided link in the notebook (See `Requirements.txt`). 

2. Open and run the API notebook and type in an amino acid sequence as input. (Notebook number 3)
