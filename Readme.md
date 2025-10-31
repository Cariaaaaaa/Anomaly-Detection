# <p align=center> Beyond Single Distillation: Bidirectional FeatureLearning with Dynamic Weighting for Robust Anomaly Localization </p>
#### Kaiyue Wang, Lu Zhang, Jieru Chi, Chenglizhao Chen, Teng Yu </sup>

 <img width="1210" height="603" alt="Fig1" src="https://github.com/user-attachments/assets/48a462f3-4f51-4ea2-beba-fc3f8a4d58ff" />
 
 ## Highlight
This study proposes an anomaly detection method that integrates forward distillation and reverse distillation. A high-performance anomaly detection
model should not only exhibit outstanding performance in single-task scenarios but also possess robust knowledge retention capability to adapt to dynamically evolving production environments.

## Introduction

In recent years, knowledge distillation-based anomaly detection shows great potential in unsupervised scenarios. Traditional isomorphic teacher-student models have two issues: similar structures weaken abnormal feature differences, and single reverse distillation ignores low-level details, limiting multi-scale anomaly capture. They also struggle with false or missed detections and local anomaly localization in complex scenes. This paper proposes a hybrid framework combining forward and reverse distillation. It uses a pre-trained teacher model and two heterogeneous students: one learns multi-scale features via forward distillation, and the other reconstructs inputs from abstract features via reverse distillation. The two students compute feature loss with the teacher for joint optimization, while a dynamic weight mechanism balances distillation losses. Compared to single distillation, this framework enhances abnormal feature distinctiveness through bidirectional comparison without complex training or annotations. Key advantages include: (1) heterogeneous students boosting anomaly feature diversity; (2) multi-scale fusion improving local anomaly localization; (3) dynamic weights enhancing robustness to complex anomalies. It offers an efficient solution for industrial inspection and medical imaging. 

## Usage

## Prerequisites

- [Python 3.5](https://www.python.org/)
- [Pytorch 1.3](http://pytorch.org/)
- [Numpy 1.15](https://numpy.org/)
- [Apex](https://github.com/NVIDIA/apex)
- [adversarial-robustness-toolbox](https://github.com/Trusted-AI/adversarial-robustness-toolbox)

## Clone repository

```shell
git clone https://github.com/Cariaaaaaa/Anomaly-Detection.git
```

## Dataset

Download the following datasets and unzip them into `data` folder

- ([MVTec Anomaly Detection Dataset: MVTec Software](https://www.mvtec.com/company/research/datasets/mvtec-ad))

## Dataset configuration

- For the training setup, update the `--dir_dataset` parameter in the `train.py` file to your training data path, e.g., `dir_dataset='./your_path/DUTS'`.
- For the testing, place all testing datasets in the same folder, and update the `--test_dataset_root` parameter in the `test.py` file to point to your testing data path, e.g., `test_dataset_root='./your_testing_data_path/'`.

## Training

```shell
    cd src/
    python3 train.py
```

- Warm-up and linear decay strategies are used to change the learning rate `lr`
- After training, the result models will be saved in `out` folder

## Testing

```shell
    cd src
    python3 test.py
```

- After testing, saliency maps of `PASCAL-S`, `ECSSD`, `HKU-IS`, `DUT-OMRON`, `DUTS-TE` will be saved in `./experiments/` folder.

## Result

+ Comparison with the previous state-of-the-art methods with different training sets:


<img width="1059" height="585" alt="results" src="https://github.com/user-attachments/assets/8b6fbe9f-097b-4689-8caa-b3344be51f42" />
