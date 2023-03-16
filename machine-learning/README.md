# Machine Learning and its limitations in seismology

Welcome to this short course on the use of machine learning in seismology. The course is designed to give you a basic understanding of machine learning and how it can be used in seismology. It is not intended to be a comprehensive course on machine learning, but rather a short introduction to the topic.

## Contents

- [Installation instructions](#installation-instructions)
  - [Python packages](#python-packages)
  - [Running the notebooks](#running-the-notebooks)
- [Datasets](#datasets)
  - [MNIST: handwritten digits](#mnist-handwritten-digits)

The present document is used for the hands-on part of the course. We will use Jupyter notebooks to run the code and to explore the data. Prior to the course, you should have installed the Anaconda Python distribution on your computer, with the following packages.

## Installation instructions

### Python packages

First, you should create a clean Python environment. This can be done by opening a terminal and typing:

    conda create --name spin-ml

This will create an empty environment called `spin-ml`. You can activate this environment by typing:

    conda activate spin-ml

By default, we will be using the channel `conda-forge` to install the packages. This can be done by typing:

    conda config --add channels conda-forge

Now we will install the one-before-last Python version, as well as the packages we will be using in the course. This can be done by typing:

    conda install python=3.10

Now we can install all the required packages. We will use primarily Numpy, Scipy, Pandas, Scikit-Learn and Matplotlib. We will also use Seaborn and PyTorch. This can be done by typing:

    conda install numpy scipy pandas scikit-learn matplotlib seaborn pytorch

<!-- We will also need to downlaod the model `PhaseNet` for the practical on earthquake seismic phase picking. To do so, we will use the `Seisbench` library which provides a convenient interface to download and process the data. This can be done by typing:

    pip install seisbench -->

### Running the notebooks

All the practicals are in the form of Jupyter notebooks, which require further packages to be installed. This can be done by typing:

    conda install jupyter

You now have several options to run the notebooks. One strategy is to use a dedicated software such as VSCode, which has a built-in Jupyter notebook interface. Another option is to use Jupyter Lab, which will run a Jupyter notebook server in your browser.

- __Using Jupyter Lab__: If you would like to use Jupyter Lab, you can install it by typing `conda install jupyterlab`. Then, follow the instructions described in the [Jupyter Lab documentation](https://jupyter.org/install) to start the server on your computer.

- __Using VSCode__: If you use VSCode, you can directly open the folder in which the Jupyter notebooks are located, and open it with the explorer. Note that running notebooks with VSCode require to install several extensions in VSCode. Please follow the instructions described in the [VSCode documentation](https://code.visualstudio.com/docs/datascience/jupyter-notebooks).

- __Using other software or converting to Python scripts__: You can also consider using other softwares to run the notebooks. For example, you can use [Google Colab](https://colab.research.google.com/) to run the notebooks in the cloud. You can also use [Binder](https://mybinder.org/) to run the notebooks in the cloud. Please refer to the documentation of these softwares to learn how to use them. The notebooks can also be converted to regular Python scripts to be run in a terminal. This can be done by typing `jupyter nbconvert --to script notebook_name.ipynb`.

## Datasets

### MNIST: handwritten digits

We will process several datasets during the practicals. We will tuse the MNIST dataset, which contains 60,000 training images and 10,000 test images of handwritten digits. This dataset is available in the `torchvision` package. You can install this package by typing:

    pip install torchvision

Once installed, you can pre-download the datasets by running the following code as a Python script, or in a Jupyter notebook, with definined a variable `DATA_DIRECTORY` to the path where you want to store the data:

```python
DATA_DIRECTORY = "./data"

# Download the MNIST train dataset
train_dataset = torchvision.datasets.MNIST(
    root=DATA_DIRECTORY,
    train=True,
    transform=transforms.ToTensor(),
    download=True,
)

# Download the MNIST test dataset
test_dataset = torchvision.datasets.MNIST(
    root=DATA_DIRECTORY,
    train=False,
    transform=transforms.ToTensor(),
    download=True,
)
```

### Seismic data

We will also understand and test several earthquake analysis deep learning models. Any seismic data you may want to bring (or already have) is welcome. If you wish to work on a dedicated seismic timeseries, we will download some from IRIS with ObsPy. You can install ObsPy by typing:

    conda install obspy

Then execute the following script from a terminal or a Jupyter notebook:

```python
from obspy.clients.fdsn import Client
from obspy import UTCDateTime

client = Client("IRIS")

# Download the data
st = client.get_waveforms(
    network="IU",
    station="ANMO",
    location="00",
    channel="BHZ",
    starttime=UTCDateTime("2019-01-01"),
    endtime=UTCDateTime("2019-01-02"),
    attach_response=True,
)
```
