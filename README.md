## Overview

This repository contains code to train a CNN model for a self driving car and run it on a simulator. The model is built on python, tensorflow and keras.

### The Simulator
We're going to use Udacity's [self driving car simulator](https://github.com/udacity/self-driving-car-sim) as a testbed for training an autonomous car.


## Installation and Dependencies

You can install all dependencies by running one of the following commands

You need a [anaconda](https://www.continuum.io/downloads) or [miniconda](https://conda.io/miniconda.html) to use the environment setting.

## Using Anaconda
```python
# Use TensorFlow without GPU
conda env create -f environments.yml

# Use TensorFlow with GPU
conda env create -f environment-gpu.yml
```


## Using pyenv & pip

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
You can install Pyenv for Windows from this [repository](https://github.com/pyenv-win/pyenv-win)
However, since it is a port, it does not have all the features, and I don't think pyenv-virtualenv exists for windows.

I would suggest going the anaconda route

#### Manual
Or you can manually install the required libraries (see the contents of the environemnt*.yml files) using pip.


## Usage


### Run the pretrained model

* Start up [the Udacity self-driving simulator](https://github.com/udacity/self-driving-car-sim) - **Download the Term1 packages**
* Choose a scene and press the Autonomous Mode button.  Then, run the model as follows:

```python
python drive.py model.h5
```

### To train the model


You'll need the data folder which contains the training images. If you don't have this, following the following steps:

1. open the Udacity Simulator and select "Training"
2. Press "R" (for record) and select the data folder in this repository as the target
3. Drive from 1-5 laps around the track
4. press "R" to stop recording, and the simulator will generate and save the data files to the folder

To train the model

```python
python model.py
```

This will generate a file `model-<epoch>.h5` whenever the performance in the epoch is better than the previous best.  For example, the first epoch will generate a file called `model-000.h5`.

Note that model.py accepts arguments such as

```
-d : data directory           : default='data'
-t : test size fraction       : default=0.2
-k : drop out probability     : default=0.5
-n : number of epochs         : default=10
-s : samples per epoch        : default=20000
-b : batch size               : default=40
-o : save best models only    : default='true'
-l : learning rate            : default=1.0e-4
```

## Credits

This is the code was developed by and used in [this](https://youtu.be/EaY5QiZwSP4) video on Youtube by Siraj Raval.

The credits for this code go to [naokishibuya](https://github.com/naokishibuya). I've merely created a wrapper to get people started.
