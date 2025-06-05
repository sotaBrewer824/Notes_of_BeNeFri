# 🎯 Kalman-Based Reward Normalization in Policy Gradient RL

This repository contains our course project on **accelerating policy gradient reinforcement learning** using Kalman-based reward normalization. We propose replacing conventional mean-std normalization with a lightweight 1D Kalman filter to stabilize training and improve sample efficiency.

📍 All notebooks are designed to be run directly in **Google Colab**, requiring no local setup.

---

## 📂 Project Structure

```
📁 Root
├── 📓 Actor Critic [CartPole] Main.ipynb
├── 📓 Proximal Policy Optimization.ipynb
├── 📓 Generalized Advantage Estimation.ipynb
├── 📓 [LunarLander]_Original.ipynb
├── 📓 [LunarLander]_KF.ipynb
├── 📁 Visualizations/
├── 📄 Final_Report.pdf
├── 📄 Presentation.pdf
```

---

## ⚙️ How to Run

Open any notebook in **Google Colab**, for example:

- [Actor Critic [CartPole] Main.ipynb](https://colab.research.google.com/)  
- [Proximal Policy Optimization.ipynb](https://colab.research.google.com/)  
- [Generalized Advantage Estimation.ipynb](https://colab.research.google.com/)

> ⚠️ No setup needed — all experiments are cloud-ready and use standard Python RL libraries.

---

## 📘 Notebooks Overview

| Notebook | Description |
|----------|-------------|
| `Actor Critic [CartPole] Main.ipynb` | PPO/AC with Kalman and mean-std reward normalization on CartPole |
| `Proximal Policy Optimization.ipynb` | PPO with ablation on normalization methods (Kalman/simple/mean-std) |
| `Generalized Advantage Estimation.ipynb` | GAE-based training under different normalization |
| `[LunarLander]_Original.ipynb` | Baseline training on LunarLander with standard normalization |
| `[LunarLander]_KF.ipynb` | Kalman-based reward normalization applied to LunarLander |

---

## 📊 Visualizations

All training plots and result figures can be found in the [`Visualizations/`](./Visualizations) folder.

Example figure:
<p align="center">
  <img src="Visualizations/ppo_cartpole_compare.png" width="600"/>
</p>

---

## 📄 Additional Materials

- 📄 `Final_Report.pdf` – Full mid-term project report with method, experiments, and analysis  
- 🎞️ `Presentation.pdf` – Slides used for project presentation

---

## 🧭 Summary

Kalman-based reward normalization provides:

- ✔️ Faster convergence in early-stage training  
- ✔️ Reduced variance in noisy environments  
- ✔️ Strong compatibility with existing RL pipelines (AC, GAE, PPO)

---

## 🔮 Future Work

- End-to-end learnable Kalman parameters $(Q, R)$  
- Multi-dimensional or state-dependent filtering  
- Extensions to continuous control, offline RL, and safe-RL

---

## 📜 License

MIT License – feel free to use and extend!
