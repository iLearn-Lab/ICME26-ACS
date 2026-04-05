# **Enhancing Diffusion-based Dataset Distillation via Adversary-Guided Curriculum Sampling**

> A curriculum-driven adversarial sampling strategy to improve diversity and performance in diffusion-based dataset distillation.

## Authors

**Lexiao Zou**<sup>1</sup>, **Gongwei Chen**<sup>1</sup>, **Yanda Chen**<sup>1</sup>, **Miao Zhang**<sup>1</sup>*

<sup>1</sup> `Harbin Institute of Technology, Shenzhen`

\* Corresponding author

## Links

* **Paper**: [`arXiv`](https://arxiv.org/abs/2508.01264)
* **Code Repository**: [`GitHub`](https://github.com/iLearn-Lab/ICME26-ACS)

---

## Table of Contents

* [Updates](#updates)
* [Introduction](#introduction)
* [Highlights](#highlights)
* [Method / Framework](#method--framework)
* [Project Structure](#project-structure)
* [Installation](#installation)
* [Usage](#usage)
* [Citation](#citation)
* [Acknowledgement](#acknowledgement)
* [License](#license)

---

## Updates

* [2025] Accepted by ICME 2025

---

## Introduction

### 背景问题

Dataset Distillation 旨在将大规模数据压缩为一个小规模“蒸馏数据集”，但在以下场景中存在明显问题：

* IPC（image-per-class）增大时性能下降
* 高分辨率数据难以有效压缩
* diffusion-based 方法存在 **样本多样性不足** 问题

### 核心思想

本文提出 **Adversary-Guided Curriculum Sampling (ACS)**，核心包括：

1. **课程式数据生成（Curriculum Sampling）**

   * 将蒸馏数据划分为多个 curriculum（阶段）
   * 从“简单 → 复杂”逐步生成数据

2. **对抗引导采样（Adversarial Guidance）**

   * 引入 discriminator
   * 用 adversarial loss 引导 diffusion 生成更多“难样本”

3. **多样性增强**

   * 减少不同生成样本之间的信息冗余
   * 提高 distilled dataset 覆盖度

### 贡献

* 提出 ACS 框架解决 diffusion 蒸馏中的多样性问题
* 结合 curriculum learning + adversarial learning
* 在 Imagewoof 和 ImageNet 上显著提升性能（+4.1%、+2.1%）
---

## Highlights

* 🚀 提升 diffusion-based dataset distillation 的性能
* 🧠 引入 curriculum learning 机制
* ⚔️ 使用 adversarial loss 提高数据多样性
* 📈 在多个 benchmark 上超过 SOTA
* 🔬 适用于 dataset compression / generative modeling 研究

---

## Method / Framework

### Framework Figure

![Framework](./assets/framework.png)

**Figure 1.** Overall framework of Adversary-Guided Curriculum Sampling (ACS).

### 方法流程概述

1. 初始化 diffusion model
2. 构建多个 curriculum（阶段）
3. 在每个阶段：

   * 使用 discriminator 提供 adversarial signal
   * 引导 diffusion 生成新样本
4. 随 curriculum 递进：

   * discriminator 不断更新
   * 生成数据逐渐复杂化

---

## Project Structure

```text
.
├── assets/                # 框架图、结果图
├── configs/               # 配置文件
├── data/                  # 数据说明
├── scripts/               # 训练/推理/评测脚本
├── src/                   # 核心方法实现
├── README.md
├── requirements.txt
└── LICENSE
```

---

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/iLearn-Lab/ICME26-ACS.git
cd ICME26-ACS
```

### 2. Create environment

```bash
python -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

---

## Usage

### Training

```bash
python scripts/train.py
```

### Dataset Distillation

```bash
python scripts/distill.py
```

### Evaluation

```bash
python scripts/eval.py
```

---

## Citation

```bibtex
@article{zou2025acs,
  title={Enhancing Diffusion-based Dataset Distillation via Adversary-Guided Curriculum Sampling},
  author={Zou, Lexiao and Chen, Gongwei and Chen, Yanda and Zhang, Miao},
  journal={2025 IEEE International Conference on Multimedia and Expo (ICME)},
  year={2025}
}
```

---

## Acknowledgement

* Thanks to the authors for their research contributions.
* Thanks to the dataset providers (ImageNet / Imagewoof).
* Thanks to the open-source community.

---

## License

This project is released under the Apache License 2.0.

