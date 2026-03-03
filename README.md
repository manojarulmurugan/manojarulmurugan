# Hey there, I'm Manoj Arulmurugan!

MS Data Science @ UW-Madison (May 2026) · Previously @ Calix & Shell India · OPT · Open to full-time DS / ML / AI roles

---

## About

I'm a data scientist who keeps getting drawn to the same class of problems: building models that actually work when a business depends on them.

My background spans production ML at Calix (forecasting ensembles, Feature Stores on Snowflake), operational analytics at Shell India, and research-oriented work in LLMs and RAG systems. I'm most energized at the intersection of rigorous modeling and real-world deployment constraints — the part where "it works in a notebook" stops being enough.

Finishing my MS this May. Currently looking for full-time roles in Data Science, ML Engineering, or Applied AI.

---

## Experience

**Machine Learning Intern — Calix, Inc.** *(Jun–Dec 2025, San Jose CA)*
Built a centralized Feature Store on Snowflake (10+ sources, 100+ features) and a forecasting ensemble (SARIMA + LSTM) that improved accuracy ~50% over baseline. Shipped to production.

**Operations Data Analyst — Shell India** *(Aug 2023–Aug 2024, Bangalore)*
Owned analytics for B2C apps. Built PowerBI dashboards on a 10TB data lake, drove $250k in cost savings. Won the Shell Mobility Wall of Fame Award Q1 2024.

---

## Featured Projects

### 🔍 Time-Aware RAG — Temporal Retrieval + Re-Ranking
Built a RAG pipeline designed for "as-of" questions — where *when* matters as much as *what*.
Fine-tuned Contriever with temporal hard negatives; built a faster MRAG re-ranker with sliding-window MaxSim + temporal decay.
**Hit@1: 59% vs 40.4% baseline** on CAQA dataset.
[→ View Project](https://github.com/manojarulmurugan)

---

### 🧠 Hallucination-Aware Steering for LLMs
Reduced hallucination rate on GPT-Neo-2.7B from 64.6% → 55.5% (+9.1pp) by training a Logistic Regression Truthfulness Separator Vector on hidden states and building a lightweight MLP probe to adapt per-token steering strength.
[→ View Project](https://github.com/manojarulmurugan)

---

### 🗺️ SquadPlanner — AI Trip Planning Agent
LangChain + Gemini AI application with 6 custom tools, processing millions of Yelp records.
Supports real-time flight/hotel APIs and budget fairness analysis for groups of 2–10 travelers.
[→ View Project](https://github.com/manojarulmurugan)

---

### 📈 Sales Forecasting + Customer Churn
ARIMA and LSTM forecasting on a 370k-record dataset with <5% error.
Churn prediction with LightGBM at 87% accuracy. End-to-end from raw data to business insight.
[→ View Project](https://github.com/manojarulmurugan/Sales-Forecasting-and-Customer-Segmentation-on-Sales-Data)

---

### 💳 Credit Risk Analysis
Stacked ensemble (RF, Naive Bayes, SVM, XGBoost) on 30k loan records — 97.7% accuracy.
Built for interpretability: actionable outputs on safe loans and profit optimization.
[→ View Project](https://github.com/manojarulmurugan/Credit-Profit-Risk-Analysis)

---

## Work in Progress

### 🛒 E-Commerce Recommendation System *(active)*
Building a full-stack ML pipeline on a 70GB+ data lake using GCS, BigQuery, and Spark on Dataproc. The goal is a production-grade recommendation system with MLFlow for experiment tracking and a GCS-based model registry.
Deliberately designed around real BigData constraints — not a toy dataset.

---

### 🗺️ SquadPlanner v2 — Expanding the Travel Agent *(active)*
Enhancing the original LangChain + Gemini AI trip planner with Google Maps integration, broader location coverage, improved UI, and new MCP + API integrations. Building toward a more robust agentic architecture.

---

## Currently Learning

- **Principles of Designing AI Agents** (Sam Bhagwat) — agentic architectures, MCP servers, tool design patterns
- **Machine Learning in Production** (DeepLearning.ai) — MLOps, model monitoring, cloud deployment pipelines

Completed: Deep Learning Specialization (DeepLearning.ai)

---

## Stack

**Languages:** Python · SQL · R · Julia
**ML/DL:** PyTorch · TensorFlow · Scikit-Learn · XGBoost · LightGBM · Hugging Face · Darts
**LLM/AI:** LangChain · RAG · Transformers · Agentic AI · MCP
**Data & Infra:** Snowflake · GCS · BigQuery · Spark · dbt · MLFlow · ETL · Feature Stores · PowerBI · Docker

---

📬 manojarulmurugan@gmail.com · [LinkedIn](https://www.linkedin.com/in/manojarulmurugan/)

### 👯‍♂️ Connect with Me
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/manojarulmurugan/)
[![Gmail](https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:manojarulmurugan@gmail.com)

🚀 **Always open to collaborate and build something amazing in AI & Data Science!**
