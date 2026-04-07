# 💰 FinAgent OpenEnv — AI Personal Finance Copilot Environment

## 🚀 Overview

**FinAgent OpenEnv** is a real-world reinforcement learning environment where AI agents learn to understand, analyze, and optimize personal finances.

Unlike toy environments, this simulates **messy, real-world financial behavior** from transaction logs (UPI, subscriptions, daily spending), requiring reasoning, categorization, and decision-making.

---

## 🎯 Problem Motivation

Individuals struggle to track where their money goes due to:

* Scattered transactions across apps (UPI, cards, subscriptions)
* Lack of structured financial summaries
* No actionable insights for budgeting

This environment enables training and evaluation of AI agents that can:

* Interpret raw financial data
* Categorize spending
* Analyze patterns
* Suggest optimized budgets

---

## 🧠 Environment Design

### 🔁 API Methods

* `reset()` → Returns initial observation
* `step(action)` → Executes action and returns (observation, reward, done, info)
* `state()` → Returns current environment state

---

## 📦 Observation Space

```json
{
  "transactions": ["Paid 450 to Swiggy", "Uber ride 120"],
  "categorized": {},
  "budget": {
    "income": 30000,
    "goal_savings": 10000
  }
}
```

---

## 🎮 Action Space

```json
{
  "action_type": "categorize | analyze | optimize | clarify",
  "payload": {}
}
```

---

## 🧩 Tasks & Difficulty Levels

### 🟢 Easy — Transaction Categorization

* Classify raw transactions into categories (food, transport, bills, etc.)
* **Goal:** Accurate classification

---

### 🟡 Medium — Spending Analysis

* Identify spending patterns and trends
* Detect high-expense categories

---

### 🔴 Hard — Budget Optimization

* Suggest actionable financial plans
* Meet savings goals under constraints
* Provide human-understandable explanations

---

## 🏆 Reward Design (0.0 – 1.0)

The environment provides **dense and meaningful rewards**:

* ✅ Correct categorization → positive reward
* 📊 Accurate analysis → partial reward
* 💡 Useful financial advice → high reward
* ❌ Incorrect assumptions → penalty
* 🔁 Helpful clarifications → small reward

Rewards are always clipped between **0.0 and 1.0**.

---

## ⚙️ Setup Instructions

### 1️⃣ Clone the repository

```bash
git clone <your-repo-url>
cd finagent-openenv
```

---

### 2️⃣ Create virtual environment

```bash
python -m venv venv
source venv/bin/activate   # Mac/Linux
venv\Scripts\activate      # Windows
```

---

### 3️⃣ Install dependencies

```bash
pip install -r requirements.txt
```

---

### 4️⃣ Set environment variables

```bash
export API_BASE_URL=https://api.openai.com/v1
export MODEL_NAME=gpt-4o-mini
export HF_TOKEN=your_api_key
```

---

### 5️⃣ Run baseline inference

```bash
python inference.py
```

Expected output:

```
[START]
[STEP] 0.4
[STEP] 0.6
[STEP] 0.8
[END]
```

---

## 🌐 Running the API Server

```bash
uvicorn run:app --reload
```

Endpoints:

* `GET /` → Health check
* `POST /reset` → Reset environment
* `POST /step` → Take action
* `GET /state` → Current state

---

## 🐳 Docker Support

```bash
docker build -t finagent-env .
docker run finagent-env
```

---

## 🤖 Baseline Agent

The provided `inference.py` uses an LLM to:

* Interpret observations
* Generate actions
* Interact with the environment

Produces reproducible baseline scores across tasks.

---

## 📊 Evaluation Criteria Alignment

This project is designed to satisfy:

* ✅ Real-world utility
* ✅ Structured OpenEnv interface
* ✅ Multi-task evaluation (easy → hard)
* ✅ Meaningful reward shaping
* ✅ Reproducible baseline
* ✅ Containerized deployment

---

## 🚀 Deployment

Hosted on Hugging Face Spaces (Docker-based deployment).

---

## 💡 Key Highlights

* Real-world financial simulation (not a toy problem)
* Multi-step reasoning environment
* Interpretable AI decision-making
* Scalable to real FinTech applications

---

## 📌 Future Improvements

* Real bank/SMS integration
* Personalized financial profiles
* Advanced anomaly detection
* Multi-agent financial planning

---

## 👨‍💻 Author

Aditya Kumar

---

## ⭐ Final Note

This environment models **real financial ambiguity and decision-making**, enabling evaluation of AI systems that are **useful, interpretable, and aligned with human needs**.
