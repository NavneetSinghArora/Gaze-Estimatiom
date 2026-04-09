# FAZE: Few-Shot Adaptive Gaze Estimation

[![Paper](https://img.shields.io/badge/arXiv-1905.01941-B31B1B.svg)](https://arxiv.org/abs/1905.01941)
[![Conference](https://img.shields.io/badge/ICCV-2019-blue.svg)](http://openaccess.thecvf.com/content_ICCV_2019/papers/Park_Few-Shot_Adaptive_Gaze_Estimation_ICCV_2019_paper.pdf)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

FAZE is a framework for few-shot adaptation of gaze estimation networks, consisting of equivariance learning (via the **DT-ED** or Disentangling Transforming Encoder-Decoder architecture) and meta-learning with gaze-direction embeddings as input. This repository contains the official implementation of our ICCV 2019 Oral presentation.

![The FAZE Framework](https://ait.ethz.ch/projects/2019/faze/banner.jpg)

---

## 🔗 Quick Links
* **Research Pages:** [NVIDIA Project Page](https://research.nvidia.com/publication/2019-10_Few-Shot-Adaptive-Gaze) | [ETH Zurich Project Page](https://ait.ethz.ch/projects/2019/faze/)
* **Media:** [ICCV 2019 Presentation](https://conftube.com/video/ByfFufRhuRc?tocitem=17) | [PDF Paper](http://openaccess.thecvf.com/content_ICCV_2019/papers/Park_Few-Shot_Adaptive_Gaze_Estimation_ICCV_2019_paper.pdf)
* **Code:** [Pre-processing Repository](https://github.com/swook/faze_preprocess)

---

## 🚀 Getting Started

### 1. Repository Setup

Clone the repository and initialize submodules:
```bash
git clone https://github.com/NavneetSinghArora/Gaze-Estimatiom.git
cd Gaze-Estimatiom
git submodule update --init --recursive
```

### 2. Prerequisites
This codebase is tested on Linux (Ubuntu). 

- **CUDA-enabled GPU** (V100 recommended for full training)
- **Python 3.x**
- **PyTorch 1.3+**
- **NVIDIA Apex** (Required for fusedSGD and DDP training)

Install Python dependencies:
```bash
pip install -r requirements.txt
```

### 3. Data Preparation
Pre-process *GazeCapture* and *MPIIGaze* datasets using the provided submodule in `preprocess/`. For detailed instructions, see [README_preprocess.md](README_preprocess.md).

---

## 🏋️ Training & Evaluation

### Download Pre-trained Weights
If you want to skip training from scratch, download the pre-trained weights for DT-ED and MAML models:
```bash
cd src/
wget -N https://ait.ethz.ch/projects/2019/faze/downloads/outputs_of_full_train_test_and_plot.zip
unzip -o outputs_of_full_train_test_and_plot.zip
```

### Execution Flow
For a complete demonstration of the pipeline, refer to the Jupyter Notebook:
👉 `Few_Shot_Gaze_Actual_Execution.ipynb`

Alternatively, run the all-in-one script:
```bash
cd src/
bash full_train_test_and_plot.bash
```

### Script Breakdown
- `1_train_dt_ed.py`: Trains the Disentangling Transforming Encoder-Decoder.
- `2_meta_learning.py`: Performs Meta-Learning for few-shot adaptation.
- `3_combine_maml_results.py`: Aggregates and plots evaluation metrics.

---

## 🎥 Realtime Demo
A live webcam demo is available in the `demo/` folder.
Check [demo/README.md](demo/README.md) for detailed setup and usage instructions.

```bash
cd demo/
python run_demo.py
```

---

## 📂 Project Structure
- `src/`: Core training and evaluation scripts.
- `demo/`: Real-time webcam demo implementation.
- `preprocess/`: Data preprocessing scripts (submodule).
- `Few-Shot_Adaptive_Gaze_Estimation.pdf`: Research paper for reference.

---

## 📜 Citation
If you find this work useful in your research, please cite our paper:

```bibtex
@inproceedings{Park2019ICCV,
  author    = {Seonwook Park and Shalini De Mello and Pavlo Molchanov and Umar Iqbal and Otmar Hilliges and Jan Kautz},
  title     = {Few-Shot Adaptive Gaze Estimation},
  year      = {2019},
  booktitle = {International Conference on Computer Vision (ICCV)},
  location  = {Seoul, Korea}
}
```

---

## 🤝 Acknowledgements
Seonwook Park carried out this work during his internship at NVIDIA. This work was supported in part by the ERC Grant OPTINT (StG-2016-717054).

