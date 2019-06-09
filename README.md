# How_to_simulate_a_self_driving_car
This is the code for "How to Simulate a Self-Driving Car" by Siraj Raval on Youtube

## Overview

This is the code for [this](https://youtu.be/EaY5QiZwSP4) video on Youtube by Siraj Raval. We're going to use Udacity's [self driving car simulator](https://github.com/udacity/self-driving-car-sim) as a testbed for training an autonomous car.

## Dependencies

You can install all dependencies by running one of the following commands

You need a [anaconda](https://www.continuum.io/downloads) or [miniconda](https://conda.io/miniconda.html) to use the environment setting.

## Using Anaconda
```python
# Use TensorFlow without GPU
conda env create -f environments.yml

# Use TensorFlow with GPU
conda env create -f environment-gpu.yml
```


## Using py-env & pip

### Installing pyenv & python 3.5.2

* [pyenv](https://github.com/pyenv/pyenv) allows you to have multiple versions on your computer.
* [pyenv-virtualenv](https://github.com/pyenv/pyenv-virtualenv) is a package that allows you to maintain differing python versions in multiple environments, making development easier and neater -

####  OSX
```
brew install pyenv
pyenv install 3.5.2
brew install pyenv-virtualenv
echo 'eval "$(pyenv init -)"' >> ~/.bash_profile
echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.bash_profile
```

if you are using `pip`, you can run

```
pyenv virtualenv 3.5.2 self-driving-3.5.2 # Creating a virtual environment with python v3.5.2
pyenv activate self-driving-3.5.2 # Starts the virtual environment
cd /path/to/dir
pip install -r requirements.txt
```

#### Windows
Or you can manually install the required libraries (see the contents of the environemnt*.yml files) using pip.


## Usage


### Run the pretrained model

* Start up [the Udacity self-driving simulator](https://github.com/udacity/self-driving-car-sim) - **Download the Term1 packages**
* Choose a scene and press the Autonomous Mode button.  Then, run the model as follows:

```python
python drive.py model.h5
```

### To train the model

You'll need the data folder which contains the training images.

```python
python model.py
```

This will generate a file `model-<epoch>.h5` whenever the performance in the epoch is better than the previous best.  For example, the first epoch will generate a file called `model-000.h5`.

## Credits

The credits for this code go to [naokishibuya](https://github.com/naokishibuya). I've merely created a wrapper to get people started.
