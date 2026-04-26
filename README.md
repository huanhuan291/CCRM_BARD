# CCRE-BARD

The official code for "CCRE-BARD Cross-Domain Complementary Recalibration with Boundary-Aware and Anatomy-Regularized Dual-stage Framework for 3D Medical Image Segmentation" ![GitHub Repo stars](     )  

 
CCRE-BARD proposes a Cross-domain Complementary Recalibration Encoder (CCRE) and a Bidirectional decoupled trAining and infeRence framework (BARD). CCRE enhances global semantic and local boundary modeling through heterogeneous feature interaction. BARD leverages boundary-aware supervision during training to improve discriminative capability, and employs lightweight structural refinement via anatomical consistency enhancement during inference. This method improves segmentation accuracy and boundary quality while maintaining good anatomical plausibility and computational efficiency.

1.We propose a Cross-Domain Complementary Recalibration Encoder(CCRE), which introduces heterogeneous feature enhancement units across different branches to enable complementary interaction and adaptive recal￾ibration of features. This design effectively improves both global semantic representation and local boundary modeling, leading to enhanced segmenta￾tion accuracy.
2.We develop a Bidirectional decoupled trAining and infeRence frame￾work (BARD), which separates boundary-aware feature learning and struc￾tural consistency optimization into two stages. Specifically, a boundary-aware supervision module (ABAS) is employed during training to enhance discriminative capability, while an anatomical consistency enhancement module (ACES) is applied during inference for lightweight structural refinement, thereby reducing optimization interference and improving both accuracy and efficiency.
3.We achieve a balanced optimization of accuracy, efficiency, and anatomical plausibility. By integrating CCRE and BARD, the proposed framework enhances boundary precision and feature discrimination while preserving topological integrity and anatomical consistency, providing a reliable and efficient solution for clinical multi-organ segmentation.

---

## Installation

1. First, clone this repository and create the environment.

```bash
git clone    
cd CCRE-BARD
conda create -n CCRE-BARD python=3.10.13
conda activate CCRE-BARD
```

Note: Before proceeding to the next step, please ensure that CUDA-11.8 is installed and its path has been added to the environment variable.

```bash
# Check CUDA version
nvcc -V  # Should return CUDA version 11.8
```

2. Install dependencies and the `mamba` package.

```bash
# Install PyTorch with CUDA 11.8
pip install torch==2.1.1 torchvision==0.16.1 torchaudio==2.1.1 --index-url https://download.pytorch.org/whl/cu118

# Install dependencies
pip install -r requirements.txt

# Install causal-conv1d
cd causal-conv1d
python setup.py install

# Install mamba
cd ../mamba
pip install -e .
```

## Usage

Main directories and files are listed below:

```
.
├── configs  # Training-related configurations
│   ├── datasets  # Dataset configurations
│   ├── models  # Model configurations
│   └── trainers  # Training hyperparameters
├── models  
│   └── CCRE-BARD_model.py  # EM-Net model
├── networks  # Comparison models
│   ├── ...
│   └── unetr.py
├── runs  # Logs and checkpoints save root
├── scripts  # Training/testing/parameter calculation scripts
│   ├── ...
│   ├── calc_params_flops.sh
│   ├── test_synapse.sh
│   └── train_synapse.sh
├── train.py  
├── test.py  
└── main.py  
```

It's easy to train and test using the provided scripts and configurations.

```bash
# Example command to run the script
sh scripts/train_synapse.sh
# or
sh scripts/test_synapse.sh  
```


## Acknowledgment

We sincerely acknowledge the following projects that provided valuable insights and resources:

- https://github.com/ge-xing/SegMamba
- https://github.com/Dao-AILab/causal-conv1d
- https://github.com/state-spaces/mamba
- https://github.com/Project-MONAI/MONAI
- https://github.com/Amshaker/unetr_plus_plus/
- https://github.com/MrYxJ/calculate-flops.pytorch

 

## License

This project is licensed under the [MIT License](LICENSE).

## Contact Us

For any questions or suggestions, please contact us at:

zhangxiaohuan@hzu.edu.cn


Or submit an issue on GitHub.

If you find this project useful, please give it a star!
