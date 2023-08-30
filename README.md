# Impact of Class Imbalance on Machine Learning Fairness

Properties of fairness measures in the context of varying class imbalance and protected group ratios

# Reproducibility

## Environment

The experiments were conducted on a machine equipped with Intel® Core™ i7-1260P 4.7GHz processor
and 48 GB of RAM, using Python 3.10.10, on Ubuntu 22.04.

The required packages, with specified versions, are listed in `requirements.txt`
and can be installed using `pip install -r requirements.txt`.

## Repository contents

In the repository, there are .py scripts for reproducing all the experiments from the paper.

All the same code is also available in the form of Jupyter notebooks, in the `notebooks/` directory,
to allow interactive execution.

### Experiments with synthetic data

- `sets_creation.py`: generation of synthetic data, consisting of all possible confusion matrices with regard to
    the protected groups and decision classes.
- `metrics_calculations`: calculation of fairness measures for synthetic data
- `histograms_plot`: distribution of fairness measures
- `perfect_fairness_and_undefined`: probability of perfect fairness and undefined values of metrics

### Experiments with real-world data

- `case_study.py`: all the code for the case study with the Adult dataset

## Code execution

### Synthetic data experiments

For the experiments with synthetic data, `sets_creation.py` and `metrics_calculations.[py|ipynb]` need to be run first
(in this specific order). The remaining scripts can be run in any order.

In the paper, we used a dataset of all possible confusion matrices of `n=56` samples. However,
the calculations take a long time and lots of RAM. For a quick check, we recommend using `n=24`. This will also
require to adjust the variable denoting the number of samples `sample_size` in `metrics_calculations`,
`histograms_plot` and `perfect_fairness_and_undefined`.

The data generation script requires two arguments:
the first should be `8` and the second one is the number of samples.
```
python sets_creation.py 8 56    # or 24, to speed up the execution
```

Other files don't take any arguments and can be run as follows:
```
python metrics_calculations.py
python histograms_plot.py
python perfect_fairness_and_undefined.py
```
They will save the results in the `out/` directory (and create it if necessary).

### Real-world data experiments

The experiments with real-world data can be found in `case_study.py`.
It uses data in `data/adult.data`, which originates from the
[UCI repository](https://archive.ics.uci.edu/ml/machine-learning-databases/adult/).

This can be run as follows:
```
python case_study.py
```
