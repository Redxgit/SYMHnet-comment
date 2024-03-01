# Prediction of the SYM-H Index Using a Bayesian Deep Learning Method with Uncertainty Quantification comment

Comment for the Prediction of the SYM-H Index Using a Bayesian Deep Learning Method with Uncertainty Quantification paper

## Author

### Armando Collado-Villaverde, Pablo Muñoz and Consuelo Cid

We provide the steps to execute the notebook on a local environment, but we heavily suggest running it in Google colab, as it frees the user from installing the dependecies and is considerably faster.

## Execution on a local machine

The dependencies to run this notebook are the same as the original repository, as such, download the original repository of the SYMHnet paper at the tag of the submission (https://github.com/ccsc-tools/SYMHnet/releases/tag/v1.0). At the time of publishing this repository, the only comment ahead of the tag only includes the DOI of the repository (https://github.com/ccsc-tools/SYMHnet/compare/v1.0...main). It can also be downloaded from the zenodo DOI: https://zenodo.org/records/10602518.

Then navigate to the downloaded folder and install the dependecies similar to the original repository

```
git clone --depth 1 --branch v1.0 https://github.com/ccsc-tools/SYMHnet
cd SYMHnet
```

* Run pip install -r requirements.txt (the file is provided within the package)<br>
* You may also use the environment.yml file to create conda virtual environment with all required packages by exeucting the following command:<br>
```
conda env create -f environment.yml 
```

Then, the notebook can be executed.

## Exeuction on Google Colab

To ensure the reproducibility of the code and to ease the execution of the notebook without installing any dependencies we have uploaded the notebook to [Google Colab](https://colab.research.google.com/).

FIX THIS LINK -->
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/weiji14/deepbedmap/)

The notebook in Colab directly downloads the Github repository so there is no need to download it to the local machine.

While the notebook can be run on CPU, it takes a considerable amount of time around 25 minutes, so we recommend to change the runtime type of the Colab notebook to use a GPU, which reduces the execution time to around 3 minutes.

## Notebook Contents

The notebook reads the prediction ``.csv`` files and plots both the Actual and Predicted SYM-H in the file. Those values are compared to the SYM-H in the ``./data`` folder which contains the CDAWeb original values.

After that, the TensorFlow model is loaded and the summary of it is printed, showing that only one time-step is used to make the forecast and it uses 11 features instead of the 8 described in the paper.

Following, we reproduce the predictions of the Test storm #37, 1 and 2 hours ahead and using the 1 and 5 minutes data, similar to the original ``run_SYMHnet.ipynb`` notebook of the official repository. We modify the test function to return the input data fed to the network, the labels, the predictions and the dates to inspect those values further. All the changes can be found in the following link: https://www.diffchecker.com/lGtAdtCk/

Finally, the input data, labels and predictions are compared for each of the 4 scenarios (1 hour ahead with 1 and 5 minutes data, 2 hours ahead with 1 and 5 minutes data). The difference between the input SYM-H and the labels is only one time-step for both the 1 and 2 hours ahead forecast. We also compute the RMSE of the predictions against the labels and the input SYM-H against the labels, emulating a persistence model. The persistence model heavily outperforms the predictions made by the SYMHnet model.
