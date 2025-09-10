# Pyrolysis_BESKID
Preparation of pyrolysis modelling publication.

## Structure
----------------------
- `DataProcessing/`: Jupyter notebooks with analysis code (sub-dirs ignored during commit)
- `Experiments/`: folder for experimental datasets  
- `GeneralInformation/`: general information, like `requirements.txt`   
- `Simulations/`: folder for simulation files


## Python Scripting
----------------------
The Python scripts are built on Python version: 3.13.3 (tags/v3.13.3:6280bb5, Apr  8 2025, 14:47:33) [MSC v.1943 64 bit (AMD64)]

Use the `requirements.txt` to build a virtual Python environment. It is located in `GeneralInformation\Python_venv`.


### How to set up a virtual Python environment on Windows
----------------------
This description assumes you intent to set up a virtual Python environment on Windows, using Powershell. Adjust the paths according to your setup.

From a clean [Python installation](https://www.python.org/downloads/), create a clean virtual environment. This is done by typing the following command into the Powershell terminal: ` C:\Programs\Python\Python313\python.exe -m venv name_of_your_environment`. You can give it a name by changing `name_of_your_environment` to what ever name you like. This will create a directory of the chosen name, containing the necessary files of the environment.

In Powershell, the process needs to be given permission to run the environment, like so:
`Set-ExecutionPolicy Unrestricted -Scope Process`
Set the exception for this process by hitting "Y" (yes). This step needs to be repeated every time you want to run the environment from your console, but is not necessary if you use it just as Jupyter kernel (see below).

Now, you can start the environment. For this, a specific file in the directory needs to be called in Powershell: `C:\Venvs\name_of_your_environment\Scripts\activate`.

The `requirements.txt` can now be used to install specific packages recursively: `pip install -r C:\Pyrolysis_BESKID\GeneralInformation\Python_venv\requirements.txt`.

You can use this virtual environment as kernel for your Jupyter notebooks. It can be installed as follows: `python -m ipykernel install --user --name=name_of_your_environment --display-name "Python (name_of_your_environment)"`.


### Set Pre-Commit Hook to Clean Jupyter Output Before Commit
----------------------

In an effort to keep the repo clean from unneccesary files, as well as binaries like images, a pre-commit hook is set up. This will [automatically remove the output of Jupyter notebooks](https://github.com/kynan/nbstripout) using `nbstripout`.

Quick checklist:

1. Have `.pre-commit-config.yaml` in the repo (with the `nbstripout` hook).
2. Install pre-commit (globally on your machine is fine, see `pipx` below): `pip install pre-commit`
3. In the repo (adds the Git hook): `pre-commit install`.
4. One-time clean (inside repo): `pre-commit run --all-files` (this should run on all files in the repo, if it does not, you can stage a notebook (`git add notebook`) and run the command)

Step 4 will set up its own environment, which can take a few minutes on the first run. For subsequent calls it will be faster then.

Now when commits are made, the hook will run before and clean the notebooks if necessary. If it removes the output of a notebook, the file is changed and the commit itself aborts. You need to stage the changed files again, as well as the commit. If the newly staged notebook is clean, it will pass.

Possible workflows:
- Inside Jupyter-lab, run `Edit\Clear Outputs of All Cells`
- Stage and commit

or

- stage notebooks
- run `pre-commit run --all-files`
- stage again
- commit, once all output is removed

or
- stage and commit (fails, because output is removed)
- stage again
- commit, once all output is removed

Notes:

- The first `run --all-files` may modify notebooks; the run can exit with a non-zero status to tell you files changed. Just `git add .` and commit afterwards.
- From now on, the hook runs on staged files at commit time and strips outputs automatically.
- Share with co-authors: they only need `pip install pre-commit && pre-commit install` in their clone.

> [!WARNING]
>
> In this mode, `nbstripout` is used as a git hook to strip any `.ipynb` files
> before committing. This also modifies your working copy!



On your machine, install `pipx` as an independent, global location for the Git hook related packages:
1. `python -m pip install --user pipx`
2. `python -m pipx ensurepath` to ensure that `~/.local/bin to PATH` is set up
3. reopen the terminal (Powershell) and run `pipx --version` to check if the path is set up correctly
4. `nbstripout` may need to be installed here too: `pipx install nbstripout`
