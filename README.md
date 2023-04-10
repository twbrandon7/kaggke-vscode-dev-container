# Kaggle-VS Code Dev Container Template for Deep Learning

[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)

## Note

This template is based on the GPU version of [Kaggle Python docker image](https://github.com/Kaggle/docker-python). To run this
template, you need to have a GPU machine with Nvidia Driver and [NVIDIA Container Toolkit installed](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html).

## Installation

1. Clone this repository and open it with Visual Studio Code.:

    ```bash
    git clone https://github.com/twbrandon7/kaggke-vscode-dev-container.git
    code .
    ```

2. Make sure you have installed Docker and Nvidia Docker toolkit in your machine. If you are using Windows, you have to
   install WSL2 and [Docker Desktop](https://www.docker.com/products/docker-desktop). In addition, you have to [install GPU driver
   for WSL2](https://learn.microsoft.com/zh-tw/windows/ai/directml/gpu-cuda-in-wsl).

   If you are using Linux, you can install Docker by following the [official guide](https://docs.docker.com/engine/install/) and install Nvidia Docker toolkit by following the [Nvidia official guide](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html).

3. Pull the latest Kaggle Pytorch image:

    ```bash
    docker pull gcr.io/kaggle-gpu-images/python:latest
    ```

    The image is about 16GB in size, so it may take a while to download.

4. Make sure [Dev Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) for VS Code extension is installed.

5. In Visual Studio Code, open the Command Palette (Ctrl+Shift+P) and select the "Remote-Containers: Reopen in Container" command to open this project.

## Start your Deep Learning project

You can create a new directory or a Jupyter Notebook in the `notebooks` directory, and start
developing your Deep Learning experiments. If there are any common modules that you want to
use in your experiments, you can create a new directory in the project root directory and
create a Python module in it. For example, if you want to create a module named `libs`, you
can create a directory named `libs` in the project root directory and create a `__init__.py`
file in it. Then, you can import the module in the notebooks by the following code:

```python
import libs
```

Note: this feature is only works with Visual Studio Code. For more information, see the
note below.

## Note for Jupyter Notebook

It is recommended to use Jupyter Notebook with Visual Studio Code. When using VScode to
open a Jupyter Notebook, the file root of each notebook in this repository is set to the
project root. So, you can import modules in the project root directory by the following
code (assuming there is a module named `libs`):

```python
import libs
```

## Note for MLflow

### Local MLflow Tracking Server

This repository uses [MLflow](https://mlflow.org/) to track experiments. You can run
the following command to start MLflow server:

```bash
mlflow ui
```

For the example usage of MLflow, see notebooks in ["./notebooks/mlflow/"](./notebooks/mlflow/) directory.

### Remote MLflow Tracking Server

When you are running an independent MLflow tracking server, you can create a `.env` file
in the project root directory and set the following environment variables:

```bash
MLFLOW_TRACKING_URI="https://mlflow.example.com/"
MLFLOW_TRACKING_TOKEN="<your token here>"
AWS_ACCESS_KEY_ID="<your key here>"
AWS_SECRET_ACCESS_KEY="<secret>"
MLFLOW_S3_ENDPOINT_URL="https://s3.example.com"
```

To load the environment variables, add the following code to the top of your Python script or notebook:

```python
from dotenv import load_dotenv

load_dotenv()
```

For the example usage of MLflow, see notebooks in ["./notebooks/mlflow/"](./notebooks/mlflow/) directory.
