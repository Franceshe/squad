## Activate
* To activate this environment, use
     $ conda activate squad
* To deactivate an active environment, use
     $ conda deactivate



## Setup

1. Make sure you have [Miniconda](https://conda.io/docs/user-guide/install/index.html#regular-installation) installed
    1. Conda is a package manager that sandboxes your project’s dependencies in a virtual environment
    2. Miniconda contains Conda and its dependencies with no extra packages by default (as opposed to Anaconda, which installs some extra packages)

2. cd into src, run `conda env create -f environment.yml`
    1. This creates a Conda environment called `squad`

3. Run `source activate squad`
    1. This activates the `squad` environment
    2. Do this each time you want to write/test your code
  
4. Run `python setup.py`
    1. This downloads SQuAD 2.0 training and dev sets, as well as the GloVe 300-dimensional word vectors (840B)
    2. This also pre-processes the dataset for efficient data loading
    3. For a MacBook Pro on the Stanford network, `setup.py` takes around 30 minutes total  

5. Browse the code in `train.py`
    1. The `train.py` script is the entry point for training a model. It reads command-line arguments, loads the SQuAD dataset, and trains a model.
    2. You may find it helpful to browse the arguments provided by the starter code. Either look directly at the `parser.add_argument` lines in the source code, or run `python train.py -h`.

## Code Review:

### The repository squad contains the following files:
* args.py: Command-line arguments for setup.py, train.py, and test.py.
* environment.yml: List of packages in the conda virtual environment.
* layers.py: Layers used by the models.
* models.py: The starter model, and any others you might add.
* setup.py: Downloads pretrained GloVe vectors and preprocesses the data.
* train.py: Top-level entrypoint for training the model.
* test.py: Top-level entrypoint for testing the model and generating submissions for the leaderboard.
* util.py: Utility functions and classes.
### In addition, you will notice two directories:
* data/: Contains our custom SQuAD dataset, both the unprocessed JSON files, and (after running setup.py), all preprocessed files.
* save/: Location for saving all checkpoints and logs. For example, if you train the baseline with python train.py -n baseline, then the logs, checkpoints, and TensorBoard events will be saved in save/train/baseline-01. The suffix number will increment if you train another model with the same name.