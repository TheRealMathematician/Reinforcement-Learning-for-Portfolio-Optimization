# Reinforcement-Learning-for-Portfolio-Optimization
Absolutely! Here's your **`README.md`** for the **Reinforcement Learning for Portfolio Optimization** project, rewritten with enhanced clarity, structure, emojis, and strong executive-level explanation — perfect for GitHub and stakeholders.


## 📘 Background and Overview

This project explores how **reinforcement learning (RL)** can be used to solve the **portfolio selection problem**, specifically under **highly volatile market conditions**. Building upon Huo’s research on **risk-aware multi-armed bandit problems**, the study develops and evaluates two key algorithms:

* 🔷 **Upper Confidence Bound (UCB)**
* 🟡 **Epsilon-Greedy (ε-greedy)**

We apply these algorithms to a **diversified portfolio of 30 stocks** (15 financial, 15 non-financial) across two historically turbulent periods:

* 📉 **2008 Global Financial Crisis**
* 🦠 **COVID-19 Market Shock (2020)**

> 🎯 The primary objective is to optimize portfolio performance by balancing the **exploration–exploitation tradeoff** under dynamic and uncertain market regimes.

---

## 🧾 Data Structure Overview

### 📊 Core Datasets

1. **🧾 Stock Price Data**

   * Source: [Yahoo Finance](https://finance.yahoo.com)
   * Time Periods:

     * Sep–Oct 2008 (Financial Crisis)
     * Mar–Apr 2020 (COVID-19)
   * Portfolio: 30 stocks (15 financials + 15 non-financials)

2. **🧠 Processed Data**

   * 30x30 **correlation matrices**
   * **Hierarchical clustering** → Cluster 1 & Cluster 2
   * Normalized **return time series**
   * Reward arrays for reinforcement learning models

### 🔄 Key Transformations

* 📈 Daily log returns
* 📉 Correlation matrix construction
* 🧬 Asset clustering via hierarchical linkage
* 🎯 Reward normalization for model input

---

## 🧠 Executive Summary

### 📌 Purpose

In dynamic financial markets, static portfolio strategies often fail to adapt to **volatility, correlation shifts, and structural breaks**. By framing portfolio selection as a **multi-armed bandit (MAB)** problem, we empower the model to **learn and adapt** through **reinforcement** — choosing actions (assets) that maximize cumulative reward over time.

> 🧠 This approach shifts from traditional mean-variance optimization to a **learning-based, adaptive system** that self-corrects based on market feedback.

---

### 🏆 Key Results and Findings

#### 📈 Algorithm Performance

| Algorithm    | Cluster 1 (Financials) | Cluster 2 (Non-Financials) |
| ------------ | ---------------------- | -------------------------- |
| **UCB**      | ✅ 1.45 Avg Return      | ✅ 1.056 Avg Return         |
| **ε-greedy** | 🔄 0.932 Avg Return    | 🔄 0.654 Avg Return        |

* ✅ UCB consistently **outperformed ε-greedy** across market conditions.
* Optimal Parameters:

  * `UCB weight c = 2`
  * `ε = 0.95` for exploration-heavy strategy

#### 🔍 Comparative Analysis

* Our approach had **lower return-error gap** vs. Huo's baseline:

  * Log-return error: `0.00032` (ours) vs `0.0045` (Huo)
* UCB showed a **better balance of exploration & exploitation**, especially in **correlated asset clusters**.

#### 🌐 Market Regime Sensitivity

* 2008 and 2020 periods revealed:

  * High **parameter sensitivity**
  * UCB's **adaptive advantage** in Cluster 1
  * ε-greedy required **higher ε** in volatile markets

#### 🧪 Parameter Insights

* UCB with `α = 4.9` gave optimal reward-return gap: `0.0788`
* ε-greedy improved with **higher exploration early on**, tapering later

---

### 🔦 Performance Highlights

| Metric           | UCB (Cluster 1) | ε-greedy (Cluster 1) | Huo Baseline |
| ---------------- | --------------- | -------------------- | ------------ |
| Avg Return       | **1.45**        | 0.932                | 0.234        |
| Avg Reward       | **1.44**        | 0.901                | 0.231        |
| Return-Reward Δ  | 0.01            | 0.031                | 0.003        |
| Optimal Action % | **2.1%**        | N/A                  | N/A          |

---

## 🔬 Insights Deep Dive

### 🔵 UCB Algorithm

* 🧠 Calculates a **confidence interval** for each asset’s reward
* Balances **exploration** (trying new assets) and **exploitation** (sticking with winners)
* Performed best in **Cluster 1 (financials)** with higher inter-asset correlation

### 🟡 ε-greedy Algorithm

* Uses a **probabilistic approach** to explore
* Needs **higher ε (0.95)** to explore during market shocks
* Less robust under high volatility (e.g., COVID period)

### 🔗 Cluster Performance

* **Cluster 1** (financial-heavy):

  * Avg correlation: **0.76**
  * Higher stability and reward
* **Cluster 2** (mixed sectors):

  * Avg correlation: **0.63**
  * More erratic behavior and lower returns

### 📉 Market Impact

* **2008 Crisis** and **2020 COVID-19** highlighted the importance of:

  * Dynamic exploration parameters
  * Sector-specific stability
  * Adaptive learning mechanisms

---

## ✅ Final Recommendations

### ⚙️ Implementation Strategy

1. **Model Choice**

   * ✅ Use **UCB with c=2** as the primary strategy
   * 🟡 Use **ε-greedy** for more volatile, exploration-driven markets

2. **Parameter Tuning**

   * UCB: Tune `α ∈ [3.5, 4.9]`
   * ε-greedy: Schedule ε dynamically (e.g., 0.95 → 0.5 over time)

3. **Production Deployment**

   * 🧭 **Real-time correlation monitoring**
   * 🔁 **Quarterly reclustering** of assets
   * 🧠 **Automated parameter tuning** based on market regimes

4. **Risk Management**

   * 💼 Position caps per cluster
   * 📉 Volatility-aware exploration
   * 📊 Benchmark tracking for model audits

---

## 🔮 Future Enhancements

1. 🧾 Integrate **macroeconomic indicators** as contextual features
2. 🧠 Implement **deep reinforcement learning (DRL)** (e.g., DQN, PPO)
3. 🔀 Develop **hybrid models** that combine UCB and ε-greedy
4. 🌐 Expand to **multi-asset portfolios** (commodities, bonds, crypto)
5. 🧬 Create a **real-time clustering engine** to reflect changing correlations

---

## 🧰 Technical Stack

| Tool         | Purpose                 |
| ------------ | ----------------------- |
| `Python`     | Core language           |
| `pandas`     | Data preprocessing      |
| `NumPy`      | Vectorized computation  |
| `scipy`      | Hierarchical clustering |
| `matplotlib` | Visualization           |
| `yfinance`   | Market data extraction  |

---

## 👥 Contributors

* 🇿🇦 Tumelo Ranoto



