# Higher-order Coreference Resolution with Coarse-to-fine Inference for the german language

## Introduction
This repository contains the german adaption from

* [Higher-order Coreference Resolution with Coarse-to-fine Inference](https://arxiv.org/abs/1804.05392)
* [Kenton Lee](http://kentonl.com/), [Luheng He](https://homes.cs.washington.edu/~luheng), and [Luke Zettlemoyer](https://www.cs.washington.edu/people/faculty/lsz)
* In NAACL 2018

## Getting Started

* Install python3 requirements: `pip3 install -r requirements.txt`
* Download pretrained model at https://drive.google.com/file/d/1L-kKxzlC0pPr_tJzRyi9xoTOKSPQXfNb/view?usp=sharing
  * Create a 'logs' folder in the root of the repository and extract the model with the folder 'final' in it.
* Download GloVe embeddings and build custom kernels by running `setup_all.sh`.
  * https://drive.google.com/file/d/1nN_qc3qHtPecxek0LsYf544ipJpfXEfj/view?usp=sharing
* To train your own models, elmo embeddings need to be trained and converted to the right format.
  * This assumes access to TüBa-D/Z dataset. 
  * https://github.com/ChristianHesels/bilm-tf

## Training Instructions

* Experiment configurations are found in `experiments.conf`
* Choose an experiment that you would like to run, e.g. `best`
* Training: `python train.py <experiment>`
* Results are stored in the `logs` directory and can be viewed via TensorBoard.
* Evaluation: `python evaluate.py <experiment>`

## Other Quirks

* It does not use GPUs by default. Instead, it looks for the `GPU` environment variable, which the code treats as shorthand for `CUDA_VISIBLE_DEVICES`.
* The training runs indefinitely and needs to be terminated manually. The model generally converges at about 400k steps.
