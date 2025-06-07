# 📘 Model-Based Reinforcement Learning Summary (Based on Lab9_c)

## ✅ 基本思想

Model-Based Reinforcement Learning（基于模型的强化学习）通过以下步骤解决 RL 问题：

1. **构建环境模型**：学习 \( P(s'|s,a) \) 和 \( R(s,a) \)，即状态转移概率和奖励函数。
2. **在模型中模拟未来**：使用学到的模型进行“规划”或“模拟”。
3. **生成策略**：通过动态规划或控制算法（如 Value Iteration）得到最优策略。

---

## 🧠 实验中的应用（Lab9_c）

实验中，你需要：

- 利用 Gym 中的环境（如 `FrozenLake`）运行多个 episode。
- 在每次 episode 中，根据 agent 的观察和动作：
  - 统计状态转移次数 \( N(s,a,s') \)
  - 累计奖励 \( R(s,a) \)
- 从这些统计中估计出：

```python
P[s, a, s'] = N(s, a, s') / sum_s' N(s, a, s')
R[s, a] = TotalReward(s,a) / N(s,a)
```

- 利用 Value Iteration 进行策略生成。

---

## 🔢 Value Iteration 核心公式

$$
V(s) = \max_a \left[ R(s,a) + \gamma \sum_{s'} P(s'|s,a) \cdot V(s') \right]
$$

最终导出策略：

$$
\pi(s) = \arg\max_a \left[ R(s,a) + \gamma \sum_{s'} P(s'|s,a) \cdot V(s') \right]
$$

---

## 🎯 优点

- ✅ **样本效率高**：可以在模型里离线规划，不需要一直交互环境。
- ✅ **可以做 planning 和 simulating**：比 model-free 方法更“聪明”。

---

## ⚠️ 缺点

- ❌ **模型不准 = 策略失败**：对模型误差非常敏感。
- ❌ **不适合高维观测**：如图像、语言等难以建模的环境。

---

## 📌 小结

| 特点           | Model-Based RL |
|----------------|----------------|
| 是否建模环境   | ✅ 是           |
| 探索方式       | 可通过模拟探索 |
| 样本效率       | ✅ 高           |
| 适用场景       | 小环境、规划型问题 |
| 难点           | 模型误差控制 & 高维建模 |

---
