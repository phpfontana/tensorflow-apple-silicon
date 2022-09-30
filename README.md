# TensorFlow on Apple Silicon

This Repo is a step-by-step guide on how to install and run TensorFlow on Apple Silicon Devices using Conda.

**Requirements:**
  - Apple Silicon Mac (M1, M1 Pro, M1 Max, M1 Ultra, M2)
  - macOS 12.3+

## Setting up Miniconda3
**Step1.** Download and install `Miniconda3` from https://docs.conda.io/en/latest/miniconda.html. Make sure to select `Miniconda3 macOS Apple M1 64-bit pkg` or `Miniconda3 macOS Apple M1 64-bit bash`. Execute and follow instalation prompts.

**Step2.** Restart Terminal

**Step3.** Open terminal and install `xcode-select` by using the following command. It is also possible to install Xcode from the App Store
```
xcode-select --install
```

## Setting up TensorFlow environment

**Step1.** Open terminal and run the following command to create a directory to setup a TensorFlow environment
```
mkdir tensorflow-apple-silicon
cd tensorflow-apple-silicon
```

**Step2.** Download and save `tensorflow-metal.yml` to `tensorflow-apple-silicon` directory and execute the following command on the terminal to create an environment with Tensorflow Metal build and dependencies installed. Make sure to `cd` into the `tensorflow-apple-silicon` directory before running the command.
```
conda env create -f tensorflow-metal.yml -n tf-metal
```

**Step3.** Activate Conda environment.
```
conda activate tf-metal
```

**Step4.** Register Conda environment to python kernel. Make sure the environment is activated while executing the command.
```
python -m ipykernel install --user --name=tf-metal --display-name "Python 3.9(tf-metal)"
```

**Step5.** Start Jupyter Notebook by running the following command on the terminal.
```
jupyter notebook
```

**Step6.** Create a new notebook by "New" -> "Notebook: Python 3.9(tf-metal)". and run the following command to verify dependencies and TensorFlow version/GPU access
```
import sys
import tensorflow as tf
import tensorflow.keras
import sklearn 
import pandas as pd

# Verifying python version | package manager | 
print(f"Python {sys.version}\n")

print(f"TensorFlow Version: {tf.__version__}")
print(f"Keras Version: {tf.keras.__version__}")
gpu = len(tf.config.list_physical_devices('GPU'))>0
print("GPU is", "available" if gpu else "NOT AVAILABLE")

print(f"\nScikit-Learn Version: {sklearn.__version__}")
print(f"Pandas Version: {pd.__version__}")
```

Output should be something like this:

```
Python 3.9.13 | packaged by conda-forge | (main, May 27 2022, 17:00:33) 
[Clang 13.0.1 ]

TensorFlow Version: 2.10.0
Keras Version: 2.10.0
GPU is available

Scikit-Learn Version: 1.1.2
Pandas Version: 1.5.0
```

