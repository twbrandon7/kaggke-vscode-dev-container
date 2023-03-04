# Deep Learning Template with Pytorch, MLflow, Black, Flake8 and isort

[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)

## Usage

Clone this repository and install dependencies by the following commands:

```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

## Recommended editor

It is recommended to use [Visual Studio Code](https://code.visualstudio.com/) with the following extensions:
- [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python)
- [Python Docstring Generator](https://marketplace.visualstudio.com/items?itemName=njpwerner.autodocstring)
- [Jupyter](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter)

## Note for Jupyter Notebook

It is recommended to use Jupyter Notebook with Visual Studio Code. The file root of each
notebook in this repository is set to the project root. So, you can import modules
in the project root directory by the following code (assuming there is a module named `libs`):

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
