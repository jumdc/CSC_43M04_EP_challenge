# Challenge: CSC_43M04_EP

This codebase allows you to jumpstart the CSC_43M04_EP data challenge. The goal is to predict the number of views a YouTube video will receive, using its thumbnail image. In addition to the thumbnail, you may also use the associated metadata (such as title and description).

# Installation
Cloning the repo:
```bash 
git clone https://github.com/jumdc/CSC_43M04_EP_challenge.git
cd CSC_43M04_EP
```


### Install conda env:
````
conda create -n challenge python=3.12
conda activate challenge
````
### Install the required packages:

1. PyTorch
    - if CUDA >= 12.4: `pip3 install torch torchvision torchaudio`
    - if CUDA = 11.8: `pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118`
    - if other set-ups check [PyTorch Quick Start](https://pytorch.org/get-started/locally/)
2. Other dependencies:
```bash
pip install -r requirements.txt
``` 

### Download the data
Download the data from kaggle and copy them in the dataset folder (unzip the files).
Note: the dataset directory content was included in the .gitignore file, and so it is not included in the repository -- won't be pushed.


# Using the codebase
This codebase aims to train models and  rely on a config management library called hydra. It allow you to have modular code where you can easily swap methods, hparams, etc.

## Training
To train your model you can run

```bash
python train.py
```

This will save a checkpoint in checkpoints with the name of the experiment you have. Careful, if you use the same exp name it will get overwritten

To add a prefix to the experiment name you can do:
```bash
python train.py prefix=your_prefix
```

## Create submission
To create a submition file, you can run:
```bash
python create_submission.py model=config_of_the_exp checkpoint_path="checkpoints/your_checkpoint.pth"
```