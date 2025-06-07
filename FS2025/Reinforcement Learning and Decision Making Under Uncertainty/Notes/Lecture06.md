# 📘 Q-Learning 与 SARSA 复习笔记（基于 Lab6）

---

## ✅ 1. Q-Learning & SARSA 的基本思想

这两种算法都属于**基于值函数的 model-free RL 方法**，目标是学出 \( Q(s, a) \)，也就是“在某状态下采取某动作的长期回报”。

---

### 🔢 Q-Learning（离策略）

更新公式：
$$
Q(s,a) \leftarrow Q(s,a) + \alpha [r + \gamma \max_{a'} Q(s', a') - Q(s,a)]
$$

- 使用“最大可能”的动作来更新 → 不管实际用了哪个动作
- 学的是最优策略（off-policy）

---

### 🔁 SARSA（在策略）

更新公式：
$$
Q(s,a) \leftarrow Q(s,a) + \alpha [r + \gamma Q(s', a') - Q(s,a)]
$$

- 用实际执行的 \( a' \) 来更新 → 与策略一致
- 学的是当前策略的值（on-policy）

---

## 📌 2. 与 Value Iteration / Policy Iteration 的关系与区别

| 比较项       | Q-Learning           | Value Iteration            |
|--------------|----------------------|-----------------------------|
| 是否需要模型 | ❌ 不需要             | ✅ 需要转移概率与奖励模型   |
| 更新方式     | TD更新               | 动态规划                   |
| 收敛目标     | \( Q^*(s,a) \)       | \( V^*(s) \), \( \pi^* \)   |
| 应用场景     | 不知道环境的情况     | 知道模型、规划任务         |

**联系：** 都通过 Bellman 方程不断逼近最优解  
**区别：** 一个是 sample-based，一个是 model-based

---

| 比较项       | SARSA               | Policy Iteration           |
|--------------|---------------------|-----------------------------|
| 是否需要模型 | ❌ 不需要            | ✅ 需要                     |
| 策略更新     | 渐进式更新           | 明确策略评估 + 提升        |
| 是否on-policy| ✅ 是                | ✅ 是                       |
| 是否收敛     | ✅（在一定条件下）   | ✅（有限状态）              |

**联系：** 都是 on-policy  
**区别：** SARSA 是“边走边学”，Policy Iteration 是“整体推理后再改策略”

---

## 🧠 3. 在考试中如何判断适用算法？

| 关键词识别 | 提示算法        |
|-------------|-----------------|
| “model-free”, “no model” | Q-Learning / SARSA |
| “sample transitions”     | Q-Learning / SARSA |
| “learns optimal policy”  | Q-Learning         |
| “follows behavior policy”| SARSA              |
| “knows transition probabilities” | Value / Policy Iteration |
| “planning” / “simulate” | Model-Based methods |

---

## ✅ 4. 哪些场景适合用 Q-learning / SARSA？

### 适合：
- 环境不可知（如：无法访问完整转移概率）
- 有交互过程（如：游戏、机器人试错）
- 在线学习（需要边探索边学习）

### 不适合：
- 已知完整 MDP 模型（此时用 Value Iteration 更高效）
- 状态空间过大（建议用函数逼近，如 DQN）
- 学习稳定性要求高（可能收敛慢）

---

## 🧪 5. Lab6 实验重点回顾

实验目标是训练一个 agent，在网格世界中学会走向目标。

- 使用 Q-learning 和 SARSA 比较收敛表现
- ε-Greedy 策略：用于平衡探索与利用
- 学到的策略随着训练轮数不断优化
- SARSA 在早期学得更安全，Q-learning 学得更激进

---

## 📌 小结

| 方法     | 是否基于模型 | 是否off-policy | 收敛目标     | 特点             |
|----------|----------------|----------------|----------------|------------------|
| Q-learning | ❌ 否         | ✅ 是          | 最优策略 \( Q^* \) | 激进探索，效率高 |
| SARSA      | ❌ 否         | ❌ 否          | 当前策略       | 稳定性更好       |

---
