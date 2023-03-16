# Machine Learning and its limitations in seismology

Welcome to this short course on the use of machine learning in seismology. The course is designed to give you a basic understanding of machine learning and how it can be used in seismology. It is not intended to be a comprehensive course on machine learning, but rather a short introduction to the topic.

The dataset used in this practical can be downloaded __here (link will be updated soon, please check back tomorrow!!__). 

The present document is used for the hands-on part of the course. We will use Jupyter notebooks to run the code and to explore the data. Prior to the course, you should have installed the Anaconda Python distribution on your computer, with the following packages.

## Installation instructions

First, you should create a clean Python environment. This can be done by opening a terminal and typing:

    conda create --name spin

This will create an empty environment called `spin`. You can activate this environment by typing:

    conda activate spin

By default, we will be using the channel `conda-forge` to install the packages. This can be done by typing:

    conda config --add channels conda-forge

Now we will install the one-before-last Python version, as well as the packages we will be using in the course. This can be done by typing:

    conda install python=3.10

Now we can install all the required packages. We will use primarily Numpy, Scipy, Pandas, Scikit-Learn and Matplotlib. We will also use Seaborn and PyTorch. This can be done by typing:

    conda install numpy scipy pandas scikit-learn matplotlib seaborn pytorch

We will also require some simple datasets from `torchvision`. You can get them with running

    pip install torchvision

## Jupyter notebooks

All the practicals are in the form of Jupyter notebooks, which require further packages to be installed. This can be done by typing:

    conda install jupyter

You now have several options to run the notebooks. One strategy is to use a dedicated software such as VSCode, which has a built-in Jupyter notebook interface. Another option is to use Jupyter Lab, which will run a Jupyter notebook server in your browser.

### Using Jupyter Lab

If you would like to use Jupyter Lab, you can install it by typing:

    conda install jupyterlab

Then, follow the instructions described in the [Jupyter Lab documentation](https://jupyter.org/install) to start the server on your computer.

### Using VSCode

If you use VSCode, you can directly open the folder in which the Jupyter notebooks are located, and open it with the explorer. Note that running notebooks with VSCode require to install several extensions in VSCode. Please follow the instructions described in the [VSCode documentation](https://code.visualstudio.com/docs/datascience/jupyter-notebooks).

### Using other software

You can also consider using other softwares to run the notebooks. For example, you can use [Google Colab](https://colab.research.google.com/) to run the notebooks in the cloud. You can also use [Binder](https://mybinder.org/) to run the notebooks in the cloud. Please refer to the documentation of these softwares to learn how to use them.

The notebooks can also be converted to regular Python scripts to be run in a terminal. This can be done by typing:

    jupyter nbconvert --to script notebook_name.ipynb
