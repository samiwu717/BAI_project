README
======
Project: Power Consumption Prediction in O-RAN Using Transfer Learning
Author:  Jiamin Wu

----------------------------------------------------------------
Repository Structure
----------------------------------------------------------------

BAI_projectcode/
│
├── dataprocessing.ipynb       # Data preprocessing pipeline
│                              # Loads raw DS1 and DS2 from origin_data/, 
│                              # applies column alignment for DS1 and condition
│                              # filtering for DS2, and exports clean_ul_with_conditions2.csv
│
├── thesis_model.ipynb         # Stage I: Model comparison on DS2
│                              # Trains and evaluates 
│                              #  Model 1 (Baseline DNN)
│                              #  Model 2 (Regularised DNN)
│                              # and Model 3 (Hybrid DNN-XGBoost)
│
├── transfer.ipynb             # Stage II: Transfer learning
│                              # Cross-platform experiments between DS1 and DS2 
│                              # using the Hybrid DNN-XGBoost model
│
├── clean_ul_with_conditions2.csv  # DS2 after preprocessing
│                                  # (output of dataprocessing.ipynb)
│
├── original_preprocess.csv        # DS1 after preprocessing
│                                  # (output of dataprocessing.ipynb)
│
└── origin_data/               # Raw datasets downloaded from their original sources (see below)

----------------------------------------------------------------
Running Order
----------------------------------------------------------------

1. dataprocessing.ipynb   -- Preprocess raw data from origin_data/
2. thesis_model.ipynb     -- Stage I model comparison
3. transfer.ipynb         -- Stage II transfer learning

----------------------------------------------------------------
Raw Data Sources (origin_data/)
----------------------------------------------------------------

DS1: O-RAN Experimental Evaluation Dataset
  File:      original_preprocess.csv
  Reference: J. X. Salvat Lozano, J. A. Ayala-Romero, L. Zanzi,
             A. Garcia-Saavedra, and X. Costa-Perez, "O-RAN
             Experimental Evaluation Datasets," IEEE DataPort,
             2022. DOI: 10.21227/64s5-q431

DS2: Virtualised Base Station Power Consumption Dataset
  File:      dataset_ul.csv
  Reference: J. A. Ayala-Romero, I. Khalid, A. Garcia-Saavedra,
             X. Costa-Perez, and G. Iosifidis, "Dataset -
             Experimental Evaluation of Power Consumption in
             Virtualized Base Stations," GitHub, 2021.
             URL: https://github.com/jaayala/power_ul_dataset

----------------------------------------------------------------
Dependencies
----------------------------------------------------------------

Python 3.10+
PyTorch       (CUDA cu118)
XGBoost
scikit-learn
pandas
numpy
matplotlib

Install via conda:
  conda create -n gpu python=3.10
  conda activate gpu
  pip install torch torchvision torchaudio
  pip install xgboost scikit-learn pandas numpy matplotlib

----------------------------------------------------------------
Notes
----------------------------------------------------------------

- GPU is recommended but not required