# Iris Neural Playground

[![Live Demo](https://img.shields.io/badge/Live_Demo-GitHub_Pages-0ea5e9?style=flat-square&logo=github)](https://razae786.github.io/Iris-MLP-Playground/)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square)](LICENSE)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-f97316?style=flat-square&logo=tensorflow)](https://tensorflow.org)
[![Python](https://img.shields.io/badge/Python-3.10%2B-38bdf8?style=flat-square&logo=python)](https://python.org)

An interactive, browser-based neural network laboratory and decision boundary engine for Multi-Layer Perceptrons (MLP). Built on top of HTML5 Canvas, modern JavaScript gradient descent routines, and empirical ablation telemetry.

**Live Application:** [https://razae786.github.io/Iris-MLP-Playground/](https://razae786.github.io/Iris-MLP-Playground/)

---

## Overview

Iris Neural Playground provides a real-time, visual breakdown of how feedforward neural networks learn non-linear boundaries. It includes live synaptic weight evolution, interactive 2D decision manifolds, multi-activation support (ReLU, Tanh, Sigmoid), and an automated 7-phase ablation benchmark (E0–E6) evaluated across multiple random seeds.

---

## Key Capabilities

* **Real-Time Gradient Descent:** Watch backpropagation adjust weights layer by layer with live loss telemetry and learning rate tuning.
* **Dynamic Decision Manifolds:** High-contrast multi-class topological surface showing real-time classification probability transitions.
* **Multi-Projection Visualizer:** Toggle between Petal Length vs. Petal Width and Sepal Length vs. Sepal Width feature projections.
* **Ablation Benchmark Suite:** Switch between 7 predefined empirical configurations isolating the causal effects of weight initializers (Glorot Uniform vs. He Normal), regularization ($L_2$ weight decay vs. Dropout), and learning rate scale ($10^{-4}$ to $10^{-2}$).
* **Early Stopping Rollback:** Interactive checkpoint indicator displaying the exact epoch where validation loss was minimized before patience exhaustion.

---

## Network Architecture

```
Input Vector [X₁, X₂, X₃, X₄]
             │
             ▼
Dense Hidden Layer (64 Neurons, ReLU / Tanh / Sigmoid)
             │
             ▼  [Optional Dropout p=0.30]
Dense Hidden Layer (32 Neurons, ReLU / Tanh / Sigmoid)
             │
             ▼  [Optional Dropout p=0.30]
Softmax Output Layer [P(Setosa), P(Versicolor), P(Virginica)]
```

* **Optimizer:** Adam
* **Objective:** Sparse Categorical Cross-Entropy
* **Regularization:** $L_2$ Kernel Regularization ($\lambda = 0.01$), Dropout ($p = 0.30$)
* **Data Preprocessing:** Stratified 60/20/20 train/validation/test split with `StandardScaler` fitted exclusively on training samples to eliminate data leakage.

---

## Empirical Benchmark Results

Evaluated over 3 random seeds with EarlyStopping (`patience=15`, `restore_best_weights=True`):

| Experiment | Configuration | Epochs Run | Best Epoch | Test Acc | Macro F1 | Δ F1 vs Base | Test Loss | Train Time |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **E0: Baseline** | Glorot, LR=0.001, No Reg | 144.3 | 133.3 | 92.22% | 0.9221 | — | 0.1812 | 23.71s |
| **E1: He Init** | He Normal, LR=0.001 | 39.7 | 24.7 | 83.33% | 0.8288 | -0.0933 | 0.2994 | 6.03s |
| **E2: L2 Reg** | Glorot, L2=0.01, LR=0.001 | 200.0 | 200.0 | 93.33% | 0.9333 | +0.0112 | 0.1158 | 25.88s |
| **E3: Dropout** | Glorot, Dropout=0.3, LR=0.001 | 78.7 | 63.7 | 90.00% | 0.8997 | -0.0224 | 0.2152 | 9.89s |
| **E4: Combined** | Glorot, L2=0.01, Drop=0.3 | 199.0 | 188.7 | 93.33% | 0.9333 | +0.0112 | 0.1287 | 24.25s |
| **E5: Low LR** | LR=0.0001, L2=0.01, Drop=0.3 | 200.0 | 200.0 | 77.78% | 0.7646 | -0.1687 | 0.3953 | 24.68s |
| **E6: High LR** | **LR=0.01, L2=0.01, Drop=0.3** | **47.0** | **32.0** | **93.33%** | **0.9333** | **+0.0112** | **0.1088** | **6.34s** |

---

## Local Setup

No external dependencies, build step, or server required:

```bash
# Clone the repository
git clone https://github.com/Razae786/Iris-MLP-Playground.git
cd Iris-MLP-Playground

# Open in browser directly
start index.html
```

---

## License

Distributed under the MIT License. See [LICENSE](LICENSE) for details.
