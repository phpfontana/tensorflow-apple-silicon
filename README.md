# TensorFlow on Apple Silicon

This Repo is a step-by-step guide on how to install and run TensorFlow on Apple Silicon Devices using Conda.

**Requirements:**
  - Apple Silicon Mac (M1, M1 Pro, M1 Max, M1 Ultra, M2)
  - macOS 12.3+

## Setting up Miniconda3
**Step1.** Download and install `Miniconda3` from https://docs.conda.io/en/latest/miniconda.html. Make sure to select `Miniconda3 macOS Apple M1 64-bit pkg` or `Miniconda3 macOS Apple M1 64-bit bash`. Execute and follow instalation prompts.

**Step2.** Open terminal and install `xcode-select` by using the following command. It is also possible to install Xcode from the App Store.
```
xcode-select --install
```

## Setting up TensorFlow environment

**Step1.** Open terminal and run the following command to create a directory to setup a TensorFlow environment.
```
mkdir tf
cd tf
```

**Step2.** Download and save `tensorflow-metal.yml` to `tf` directory and execute the following command on the terminal to create an environment with Tensorflow Metal build and dependencies installed. Make sure to `cd` into the `tf` directory before running the command.
```
conda env create -f tensorflow-metal.yml -n tf
```

**Step3.** Activate Conda environment.
```
conda activate tf
```

**Step4.** Register Conda environment to python kernel. Make sure the environment is activated while executing the command.
```
python -m ipykernel install --user --name=tf --display-name "Python 3.9 (tf)"
```

**Step5.** Start Jupyter Notebook by running the following command on the terminal.
```
jupyter notebook
```

**Step6.** Create a new notebook by with "Python 3.9 (tf)" kernel.

**Step7.** Run the following command to verify dependencies and TensorFlow version/GPU access
```
import sys
import tensorflow as tf
import tensorflow.keras

# Verifying python version | package manager | 
print(f"Python {sys.version}\n")

print(f"TensorFlow Version: {tf.__version__}")
print(f"Keras Version: {tf.keras.__version__}")
gpu = len(tf.config.list_physical_devices('GPU'))>0
print("GPU is", "available" if gpu else "not available")

```

Output should be something like this:

```
Python 3.9.13 | packaged by conda-forge | [Clang 13.0.1 ]

TensorFlow Version: 2.10.0
Keras Version: 2.10.0
GPU is available

```

