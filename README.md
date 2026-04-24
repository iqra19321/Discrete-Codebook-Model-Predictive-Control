# Benchmarking Discrete Codebook MPC on DeepMind Control Suite

This repository contains a comparative study of **Discrete Codebook Model Predictive Control (DC-MPC)** against state-of-the-art model-based RL algorithms: **TD-MPC2** and **DreamerV3**. All agents are evaluated on the `pendulum_swingup` task from the **DeepMind Control (dm_control)** suite.

---

## Project Objectives
The goal of this research is to evaluate how different latent space representations affect planning and control efficiency.
* **DC-MPC:** Uses Finite Scalar Quantization (FSQ) to learn a discrete codebook world model.
* **TD-MPC2:** A baseline using a continuous latent space with joint representation and value learning.
* **DreamerV3:** A baseline using categorical (one-hot) latent variables and world model imagination.

---

## Experimental Setup
To ensure a fair comparison, all three agents were trained under the following constraints:
* **Environment:** `dm_control` Pendulum Swingup.
* **Training Budget:** 100,000 steps per agent.
* **Evaluation Metric:** Episode Return (Cumulative Reward).
* **Architecture Detail:** DC-MPC utilizes an FSQ-based bottleneck to quantize the world model's state representation.

---

## Results & Findings
The results demonstrate that DC-MPC achieves a stable "Swingup Plateau" comparable to (or exceeding) the baselines within the 100k step budget.

| Agent | Latent Type | Training Steps | Status |
| :--- | :--- | :--- | :--- |
| **DC-MPC (Ours)** | Discrete Codebook (FSQ) | 100,000 | Stable Plateau Achieved |
| **TD-MPC2** | Continuous | 100,000 | Successfully Replicated |
| **DreamerV3** | Categorical (One-hot) | 100,000 | Successfully Replicated |

### Performance Visualization
The training curve in `DC_MPC_PENDULUM.ipynb` shows the DC-MPC agent successfully mastering the swingup maneuver at approximately 40-50k steps and maintaining high returns through the 100k mark.

---

## Repository Content
* **DC_MPC_PENDULUM.ipynb**: Implementation of the Discrete Codebook agent and FSQ logic.
* **TDMPC2_PENDULUMN.ipynb**: Implementation of the TD-MPC2 baseline.
* **DreamerV3_Pendulumn.ipynb**: Implementation of the DreamerV3 baseline.
* **Model Checkpoints**: `*.pt` files containing saved weights after 100k steps.

---

## How to Run
1. **Environment:** Ensure `dm_control` and `mujoco` are installed.
2. **Dependencies:** `torch`, `fsq`, `numpy`, `matplotlib`.
3. **Execution:** Each notebook is self-contained. Open and run the cells to see the training logs and final evaluation videos.

---

## Authors
**Iqra Yousuf & Fareeha Fatima** *RL Research Assignment*
