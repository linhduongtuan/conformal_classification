<p align="center"><img width=25% src="https://github.com/aangelopoulos/conformal-classification/blob/master/media/logo_conformal.svg"></p>
<p align="center"><img width=60% src="https://github.com/aangelopoulos/conformal-classification/blob/master/media/text_conformal.svg"></p>

<p align="center">
    <a href="" alt="Python"> <img src="https://img.shields.io/badge/python-v3.6+-blue.svg" /> </a>
    <a href="" alt="Dependencies"> <img src="https://img.shields.io/badge/dependencies-up%20to%20date-brightgreen.svg" /> </a>
    <a href="https://opensource.org/licenses/MIT" alt="License"> <img src="https://img.shields.io/badge/license-MIT-blue.svg" /> </a>
</p>

## Citation
[Uncertainty Sets for Image Classifiers using Conformal Prediction](https://arxiv.org/abs/)
```
@article{angelopoulos2020event,
  title={Event Based, Near Eye Gaze Tracking Beyond 10,000 Hz},
  author={Angelopoulos, Anastasios N and Martel, Julien NP and Kohli, Amit PS and Conradt, Jorg and Wetzstein, Gordon},
  journal={arXiv preprint arXiv:2004.03577},
  year={2020}
}
```

## Basic Overview

<p>
    This codebase modifies any Pytorch classifier to output a <i>predictive set</i> which provably contains the true class with a probability you specify.
    The procedure is as simple and fast as Platt scaling, but provides a formal guarantee for every model and dataset.
</p>

<figure>
<img src="https://github.com/aangelopoulos/conformal-classification/blob/master/media/figure_sets.svg" alt="Set-valued classifier." style="display: block; width=80%">
<figcaption>
    The figure caption.
</figcaption>
</figure>

<br>

## Usage
From the root directory, install the dependencies and run our example by executing:
```
git clone https://github.com/aangelopoulos/conformal-classification
conda env create -f environment.yml
source activate conformal
python example.py
```
If you'd like to use our codebase on your own model, first place this at the top of your file:
```
from conformal.py import *
from utils.py import *
```
Then create a holdout set for conformal calibration using a line like: 

[`calib, val = random_split(mydataset, [num_calib,total-num_calib])` ](https://github.com/aangelopoulos/conformal-classification/blob/b3823a924bbd039b60bf5a37e517ca87f598fdbe/example.py#L39)

Finally, you can choose `kreg` and `lamda` and conformalize your model with, e.g.,

[`model = ConformalModel(model, calib_loader, alpha=0.1, kreg=4, lamda=0.1)`](https://github.com/aangelopoulos/conformal-classification/blob/b3823a924bbd039b60bf5a37e517ca87f598fdbe/example.py#L53)
