# TensorFlow on Apple Silicon

This Repo is a step-by-step guide on how to install and run TensorFlow on Apple Silicon Devices using Conda.

**Requirements:**
  - Apple Silicon Mac (M1, M1 Pro, M1 Max, M1 Ultra, M2)
  - macOS 12.3+

## Removing Conda Environment (Optional)
**Step1.** open terminal and run the following command to install `anaconda-clean` package. this package will uninstall anaconda distribution, which includes anaconda and miniconda.
```
conda install anaconda-clean
```

**Step2.** run the one of the following commands to remove miniconda/anaconda

```
anaconda-clean

anaconda-clean --yes
```
**Step3.** there might be a few files left behind. To fix this, we can simply drag the remaining files to the trash.

## Setting up Miniconda3
**Step1.** Download and install `Miniconda3` from https://docs.conda.io/en/latest/miniconda.html. make sure to select `Miniconda3 macOS Apple M1 64-bit pkg` or `Miniconda3 macOS Apple M1 64-bit bash`. 

**Step2.** Restart Terminal and install `xcode-select` by using the following command. It is also possible to install Xcode from the App Store
```
xcode-select --install
```

## Setting up TensorFlow environment

**Step1.** Open terminal and run the following command to create a directory to setup a TensorFlow environment
```
mkdir tensorflow-apple-silicon
cd tensorflow-apple-silicon
```

**Step2.** Download and save `tensorflow-metal.yml` to `tensorflow-apple-silicon` directory and execute the following command on the terminal to create an environment with Tensorflow Metal  build and dependencies installed. Make sure to `cd` into the `tensorflow-apple-silicon` directory before running the command.
```
conda env create -f tensorflow-metal.yml -n tf-metal
```

**Step3.** Activate Conda environment.
```
conda activate tf-metal
```

**Step4.** Register Conda environment to python kernel. Make sure the environment is activated.
```
python -m ipykernel install --user --name=tf-metal --display-name "Python 3.9(tf-metal)"
```

**Step5.** Start Jupyter Notebook by running the following command on the terminal.
```
jupyter notebook
```

**Step6.** Create a new notebook by "New" -> "Notebook: Python 3.9(tf-metal)". and run the following command to verify dependencies and TensorFlow version/GPU access
```

```


