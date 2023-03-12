# Hello!

Below you can find a outline of how to reproduce my solution for the WiDs Datathon 2023 competition.
If you run into any trouble with the setup/code or have any questions feel free to contact me.

# CONTENTS
prepare_data.py     :  This code run does preprocessing methods applied to the data__
train.py            :  This code trains the data on 4 models__
predict.py          :  This code predicts the test data__

# HARDWARE
Processor  : Intel(R) Core(TM) i5-10300H CPU @ 2.50GHz, 2496 Mhz, 4 Core(s), 8 Logical Processor(s)__
RAM        : 16.0 GB 2667MHz__
GPU        : NVIDIA GeForce GTX 1650__

# SOFTWARE (python packages are detailed separately in `requirements.txt`):
Python 3.10.10

# DATA SETUP (assumes the [Kaggle API](https://github.com/Kaggle/kaggle-api) is installed)
mkdir -p data/raw/__
cd data/raw/__
kaggle competitions download -c widsdatathon2023 -f train_data.csv__
kaggle competitions download -c widsdatathon2023 -f test_data.csv__

# DATA PROCESSING
Expected to run for 5 minutes__
Uses psuedo labeling from a previously trained model__
Includes few features extraction and feature selections__
Saves 4 files, 2 training files and 2 test files each test and train contains a certain set of features__
To run the code for preprocessing: python ./prepare_data.py__

# MODEL BUILD
Model building is expected to run for 1 hour__
Contains 2 lightgbm models and 2 catboost models, each of these 2 models trained on the cleaned trained data__
The 4 models are saved in models folder__
To run the code for model building: python ./train.py__

# MODEL PREDICTIONS
Model predictions should come out instantly__
The code reads the cleaned test files, and the built models for predictions__
Each model predicts the result and then the predictions are ensembled together__
The latest predictions are then saved in the submission folder__
To run the code for model predictions: python ./predict.py__
