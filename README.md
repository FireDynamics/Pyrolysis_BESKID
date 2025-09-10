# Pyrolysis_BESKID
Preparation of pyrolysis modelling publication.


## Python Scripting

The Python scripts are built on Python version: 3.13.3 (tags/v3.13.3:6280bb5, Apr  8 2025, 14:47:33) [MSC v.1943 64 bit (AMD64)]

Use the `requirements.txt` to build a virtual Python environment. It is located in `GeneralInformation\Python_venv`.

### How to set up a virtual Python environment on Windows

This description assumes you intent to set up a virtual Python environment on Windows, using Powershell. Adjust the paths according to your setup.

From a clean [Python installation](https://www.python.org/downloads/), create a clean virtual environment. This is done by typing the following command into the Powershell terminal: ` C:\Programs\Python\Python313\python.exe -m venv name_of_your_environment`. You can give it a name by changing `name_of_your_environment` to what ever name you like. This will create a directory of the chosen name, containing the necessary files of the environment.

In Powershell, the process needs to be given permission to run the environment, like so:
`Set-ExecutionPolicy Unrestricted -Scope Process`
Set the exception for this process by hitting "Y" (yes). This step needs to be repeated every time you want to run the environment from your console, but is not necessary if you use it just as Jupyter kernel (see below).

Now, you can start the environment. For this, a specific file in the directory needs to be called in Powershell: `C:\Venvs\name_of_your_environment\Scripts\activate`.

The `requirements.txt` can now be used to install specific packages recursively: `pip install -r C:\Pyrolysis_BESKID\GeneralInformation\Python_venv\requirements.txt`.

You can use this virtual environment as kernel for your Jupyter notebooks. It can be installed as follows: `python -m ipykernel install --user --name=name_of_your_environment --display-name "Python (name_of_your_environment)"`.
