# Iris MLP Playground & Ablation Study 🌸🧠

[![Live Demo](https://img.shields.io/badge/Live_Demo-GitHub_Pages-2ea44f?style=for-the-badge&logo=github)](https://razae786.github.io/Iris-MLP-Playground/)
[![Python](https://img.shields.io/badge/Python-3.10%2B-blue?style=for-the-badge&logo=python)](https://python.org)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange?style=for-the-badge&logo=tensorflow)](https://tensorflow.org)
[![Author](https://img.shields.io/badge/Author-Raza_e_Mustafa_(FA23--BAI--064)-purple?style=for-the-badge)](https://github.com/Razae786)

An interactive, browser-based **TensorFlow Playground-style visualizer** designed specifically for Multi-Layer Perceptron (MLP) classification on Fisher's Iris dataset, backed by a comprehensive **7-phase ablation study (E0 to E6)** evaluated over 3 random seeds.

🌐 **Experience the Live Interactive Web Visualizer:**  
👉 **[https://razae786.github.io/Iris-MLP-Playground/](https://razae786.github.io/Iris-MLP-Playground/)**

---

## 🚀 Key Features

* 🧠 **Live Neural Network Topology:** Visualizes input features ($4$), hidden layers ($64 \to 32$), and output softmax probabilities ($3$) with animated synaptic weights.
* 🎨 **Dynamic 2D Decision Boundaries:** Real-time multi-class decision space (Teal for *Setosa*, Amber for *Versicolor*, Purple for *Virginica*) that warps and sharpens during gradient descent.
* 📉 **Real-Time Loss Curves:** Plots Training Loss vs. Validation Loss with an exact **EarlyStopping Rollback marker**.
* 🔬 **7 Ablation Configurations:** Easily toggle between baseline, initialization methods (Glorot vs. He Normal), regularization ($L_2$ vs. Dropout), and learning rate magnitudes ($10^{-4}$ to $10^{-2}$).

---

## 🏛️ Model Architecture

```text
Input Features (4) 
   │
   ▼
Dense Layer (64 units, ReLU) ──> Dropout (p)
   │
   ▼
Dense Layer (32 units, ReLU) ──> Dropout (p)
   │
   ▼
Output Layer (3 units, Softmax) ──> [Setosa, Versicolor, Virginica]
```

* **Optimizer:** Adam
* **Loss Function:** Sparse Categorical Cross-Entropy
* **Early Stopping:** `patience=15`, `restore_best_weights=True`
* **Data Preprocessing:** Stratified 60/20/20 split with `StandardScaler` fitted strictly on `X_train` to prevent data leakage.

---

## 📊 Empirical Ablation Results (3 Seeds Mean)

| Experiment | Configuration | Epochs Run | Best Epoch | Test Acc (%) | Test Macro F1 | Δ F1 vs Base | Test Loss | Time (s) |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **E0: Baseline** | Glorot, LR=0.001, No Reg | 144.3 | 133.3 | 92.22% | 0.9221 | — | 0.1812 | 23.71s |
| **E1: He Init** | He Normal, LR=0.001 | 39.7 | 24.7 | 83.33% | 0.8288 | -0.0933 | 0.2994 | 6.03s |
| **E2: L2 Reg** | Glorot, L2=0.01, LR=0.001 | 200.0 | 200.0 | 93.33% | 0.9333 | +0.0112 | 0.1158 | 25.88s |
| **E3: Dropout** | Glorot, Dropout=0.3, LR=0.001 | 78.7 | 63.7 | 90.00% | 0.8997 | -0.0224 | 0.2152 | 9.89s |
| **E4: Combined** | Glorot, L2=0.01, Drop=0.3 | 199.0 | 188.7 | 93.33% | 0.9333 | +0.0112 | 0.1287 | 24.25s |
| **E5: Low LR** | LR=0.0001, L2=0.01, Drop=0.3 | 200.0 | 200.0 | 77.78% | 0.7646 | -0.1687 | 0.3953 | 24.68s |
| **⭐ E6: High LR** | **LR=0.01, L2=0.01, Drop=0.3** | **47.0** | **32.0** | **93.33%** | **0.9333** | **+0.0112** | **0.1088** | **6.34s** |

> **🏆 Winner: Experiment E6** achieved the lowest test cross-entropy loss (**0.1088**) and highest Macro F1 (**0.9333**) while converging **4x faster** than baseline!

---

## 💻 Running Locally

Simply clone the repository and open `index.html` in any web browser:

```bash
git clone https://github.com/Razae786/Iris-MLP-Playground.git
cd Iris-MLP-Playground
# Double-click index.html or serve locally:
python -m http.server 8000
```

---

## 👤 Author

* **Raza e Mustafa** (FA23-BAI-064)  
* BS Artificial Intelligence  
* GitHub: [@Razae786](https://github.com/Razae786)
