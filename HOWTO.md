# Python ML project skeleton

**THIS HAS NOT BEEN VALIDATED YET**

TODO: full update of this file

This is an opinionated project skeleton for a Python based machine learning
projects. This skeleton is to be used as the default project start for any
Python project (unless arguments supporting otherwise).

While this project is heavily opinionated, opinions can be discussed:
feel free to open an issue for this.

This project is built upon the best practices discussed in
our [methodology](https://gitlab.com/dataroots/public/methodology) repo.

## How-to

### Setup the environment

TODO: 
- add docker-compose instructions (and how to setup pycharm to use this container)
- conda example
- pip example

### Using Jupyter for exploratory work

TODO: add docker-compose instructions

### Makefile

TODO: UPDATE

Try out the `make` commands on the example iris dataset model (see
`make help`).

```sh
clean_environment              remove the associated conda environment
count_report_files             count the number of present report files
count_test_files               count the number of present test files
create_environment             create a conda environment
generate_dataset               run new ETL pipeline
help                           show help on available commands
init                           create environment & install requirements.txt
lint                           lint the code using flake8
prediction                     predict new values, you can pass arguments as follows: make ARGS="--foo 10 --bar 20" train
pytest                         run tox/pytest tests
requirements                   install requirements specified in "requirements.txt"
test                           run extensive tests
train                          train the model, you can pass arguments as follows: make ARGS="--foo 10 --bar 20" train
```

Note the dependency: `generate_dataset` > `train` > `prediction`.

## Overview project structure

```
├── data
│   ├── predictions
│   ├── raw
│   ├── staging
│   └── transformed
├── models
│   └── metadata
├── notebooks
├── reports
├── src
│   ├── etl
│   ├── helpers
│   └── model
└── tests

```

## Project configuration


Add configuration variables to the `.env` file. Note, check to see if it's OK
to include this in the git repository. No credentials should be committed.

## Project content

### data/

Location for data in various shapes (see directory structure).
Note that the `raw` data should always be considered **immutable**.

For larger projects, where it's infeasible to have project specific datasets
within the project structure, make sure to update the configuration and
connectors to reflect as much.

### models/

Location of saving of pickled models. Note, default to saving models in a git
repository in order to log a git commit hash when building predictions or
evaluation model training. Make sure that the serialized version is of a
reasonable size (e.g., do not include training data in the model object).

Metadata about models is about to be stored in `models/metadata`. See the
included example for more information.s

### notebooks/

Location to save notebooks used for data and model exploration.

### reports/

Location for reports and files necessary to reproduce report generation.
Note that non-Python tools (e.g. RMarkdown) can be used as well.

At least a explorative and delivery report are expected.

Note that `make test` will not error if reports are not included, but will
instead issue a warning.

### src/

This directory should contain the logic for the model (training & prediction),
ETL, helpers and potential apps. All source code relevant to a packaged
and deployable delivery should be contained in this folder.

### tests/

This directory contains the unittest by which you test your helper functions
and (deployed) model performance.

## Best practices for development

- Make sure that `make test` runs properly.
- Commit often, perfect later.
- Integrate `make test` with your CI pipeline.
- Capture `stdout` when deployed.