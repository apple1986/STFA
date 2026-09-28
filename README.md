# README.md
# Structural Tensor and Frequency Guided Semi-Supervised Segmentation for Medical Images
Xuesong Leng, Xiaxia Wang, Wenbo Yue, Jianxiu Jin, Guoping Xu

## Introduction
This repository provides the official implementation of **Structural Tensor and Frequency Guided Semi-Supervised Segmentation (STFA)** for medical image segmentation. The STFA framework exploits structural tensor to capture local geometric features and frequency-domain regularization to improve segmentation performance under limited labeled medical data.

## Installation
This repository has been tested on **Ubuntu 22.04**. We recommend using `conda` to manage the Python environment.

### Create Conda Environment
```bash
conda create -n STFA python=3.10
conda activate STFA
```

### Install PyTorch
> PyTorch 2.0.0 is recommended. Please select the CUDA version compatible with your NVIDIA driver. You can check your available CUDA version via `nvidia-smi`.
```bash
conda install pytorch torchvision torchaudio pytorch-cuda=11.8 -c pytorch -c nvidia
```

### Install Python Dependencies
```bash
pip install -r requirements.txt
```

## How to Use the STFA Model for Medical Image Segmentation
### 1. Data Preparation
1. Organize your medical image dataset following the data structure defined in the code.
2. Modify the dataset path and related parameters in the configuration file or `train_STFA.py` to point to your own medical images.
3. Split the dataset into labeled training set, unlabeled training set and test set as required by semi-supervised learning.

### 2. Model Training (Semi-supervised Training)
Run the training script to train the STFA model on your medical dataset:
```bash
python train_STFA.py
```
> During training, the model uses both labeled images and unlabeled images, guided by structural tensor and frequency constraints. Model checkpoints will be saved automatically.

### 3. Model Inference & Testing
After training completes, use the saved checkpoint to perform medical image segmentation inference on test images:
```bash
python test_fully.py
```
- The script will load the trained STFA checkpoint.
- Perform segmentation prediction on your test medical images.
- Output segmentation masks and quantitative evaluation metrics (Dice, IoU, etc., if supported).

## Citation
This work was published in *Medical Physics*. If you find this repository useful for your research, please cite our paper:
```bibtex
@article{leng2024structural,
  title={Structural tensor and frequency guided semi-supervised segmentation for medical images},
  author={Leng, Xuesong and Wang, Xiaxia and Yue, Wenbo and Jin, Jianxiu and Xu, Guoping},
  journal={Medical Physics},
  volume={51},
  number={12},
  pages={8929--8942},
  year={2024},
  publisher={Wiley Online Library}
}
```

## Paper Reference
Leng, X., Wang, X., Yue, W., Jin, J., & Xu, G. (2024). Structural tensor and frequency guided semi‐supervised segmentation for medical images. *Medical Physics*, 51(12), 8929-8942.

## Notes
- Adjust hyperparameters (learning rate, batch size, frequency loss weight, structural tensor settings) according to your imaging modality (CT/MRI etc.) and target organ.
- Ensure your medical images are preprocessed (resampling, intensity normalization) consistently with the paper.

---
