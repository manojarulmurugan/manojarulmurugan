<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0575E6,100:00c6ff&height=130&section=header&text=Manoj%20Arulmurugan&fontSize=38&fontColor=ffffff&fontAlignY=60&desc=Data%20Scientist%20%7C%20ML%20Engineer%20%7C%20UW-Madison%20%2726&descAlignY=80&descSize=15&descColor=dde8ff" />

### 📍 MS Data Science @ UW-Madison (May 2026) &nbsp;·&nbsp; Previously @ Calix & Shell India &nbsp;·&nbsp; Open to full-time roles

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/manojarulmurugan/)
[![Gmail](https://img.shields.io/badge/Gmail-manojarulmurugan@gmail.com-D14836?style=flat-square&logo=gmail&logoColor=white)](mailto:manojarulmurugan@gmail.com)

</div>

---

## 👋 About Me

ML and AI person at heart, with a foundation in production systems and an eye on where the field is heading.

Data makes real-world problems tangible to me. When I can see a problem through numbers, patterns, and structure, solving it becomes genuinely exciting, and that's what keeps pulling me deeper into this field.

I care about the full arc: from modeling to deployment, from classical ML to agentic systems and LLMs. I've shipped real ML systems in industry, worked across time-series, deep learning, and retrieval-based AI, and I'm actively building in MLOps, NLP, and agentic AI because that's where things are getting interesting.

> 🎓 Finishing my MS this May. Actively looking for full-time roles in **Data Science, ML Engineering, or Applied AI**.

---

## 💼 Experience

### 🔷 Machine Learning Intern @ Calix, Inc. *(Jun–Dec 2025 · San Jose, CA)*
- Architected a centralized **Feature Store on Snowflake** integrating **10+ data sources** and **100+ engineered features**
- Built a forecasting ensemble (account-level regression + **SARIMA + LSTM**), achieving **~50% improvement in forecast accuracy** over baseline. **Shipped to production.**
- Applied **Genetic Algorithm-based feature selection**, reducing dimensionality by **~80%**
- Optimized pipelines to cut model runtime **~30%** to meet real warehouse cost and timeout constraints

### 🔷 Operations Data Analyst @ Shell India *(Aug 2023–Aug 2024 · Bangalore)*
- Owned operational analytics for B2C apps; cut team workload **50%** through process improvements
- Built **PowerBI dashboards** on a **10TB data lake** via SQL, driving **$250,000 in cost savings**
- Engineered automated **ETL pipelines**, accelerating data processing **3x**
- 🏆 **Shell Mobility Wall of Fame Award, Q1 2024**

---

## 🚀 Featured Projects

| Project | What it does | Key Result |
|---|---|---|
| 🔍 [Time-Aware RAG](#-time-aware-rag) | Temporal retrieval pipeline for "as-of" QA | **Hit@1: 59% vs 40.4% baseline** |
| 🧠 [Hallucination Steering](#-hallucination-aware-steering) | LLM truthfulness via hidden-state steering | **Hallucination rate: 64.6% → 55.5%** |
| 🗺️ [SquadPlanner](#-squadplanner) | AI trip planning agent with LangChain + Gemini | 6 tools · millions of Yelp records |
| 📈 [Sales Forecasting + Churn](#-sales-forecasting--churn) | ARIMA/LSTM + LightGBM on 370k records | **<5% forecast error · 87% churn accuracy** |
| 💳 [Credit Risk Analysis](#-credit-risk-analysis) | Stacked ensemble on 30k loan records | **97.7% accuracy** |
| 🧩 [Fall Detection System](#-fall-detection-system) | ConvLSTM + LRCN on 46GB video data | **82% accuracy** |

---

### 🔍 Time-Aware RAG: Temporal Retrieval + Re-Ranking
> *Retrieval-Augmented Generation · NLP · Information Retrieval*

Most RAG systems ignore *when* a fact was true. This one doesn't.

- Built a pipeline for **"as-of / when"** questions using year-anchored FineWeb-Edu Q–passage pairs
- Fine-tuned **Contriever** with temporal hard negatives via triplet margin loss to cut time-mismatched retrieval
- Built a faster **MRAG re-ranker** using Sliding-Window MaxSim + temporal-decay fusion

**📊 Hit@1: 59% (vs 40.4% baseline) on CAQA · In-domain: 84.9%**

[→ View Project](https://github.com/manojarulmurugan/Time-Aware-Retrieval-Augmented-Generation)

---

### 🧠 Hallucination-Aware Steering for LLMs
> *LLM Safety · Interpretability · Hallucination Mitigation*

- Trained a **Logistic Regression Truthfulness Separator Vector (TSV)** on hidden states, replacing centroid/OT steering
- Built a lightweight **MLP hallucination-risk probe** to adapt per-token steering strength, capped to prevent logit explosion
- Steered only **~57% of tokens**, keeping fluency intact

**📊 TruthfulQA on GPT-Neo-2.7B: 64.6% → 55.5% hallucination rate (+9.1pp improvement)**

[→ View Project](https://github.com/manojarulmurugan/Probe-Controlled-TSV)

---

### 🗺️ SquadPlanner: AI Trip Planning Agent
> *LLM Agents · LangChain · Gemini AI*

- **6 custom tools** processing millions of Yelp records for personalized itineraries
- Real-time **flight & hotel API** integration + **budget fairness analysis** for groups of 2–10 travelers
- Built an ETL pipeline processing the Yelp Dataset into a structured activities DB with semantic tagging

[→ View Project](https://github.com/manojarulmurugan/AI-Squad-Planner)

---

### 📈 Sales Forecasting + Customer Churn
> *Time-Series · Classification · Business Analytics*

- **ARIMA + LSTM** forecasting on a **370,000-record** sales dataset with **<5% forecast error**
- Applied ECDF for churn definition and customer lifecycle analysis
- **LightGBM + RandomForest** churn prediction at **87% accuracy**

[→ View Project](https://github.com/manojarulmurugan/Sales-Forecasting-and-Customer-Segmentation-on-Sales-Data)

---

### 💳 Credit Risk Analysis
> *Machine Learning · Ensemble Methods · Fintech*

- Processed **30,000 loan records** to predict credit risk using a **stacked ensemble** (RF + Naive Bayes + SVM + XGBoost)
- Delivered actionable insights on safe loans and optimized profit potential for financial institutions

**📊 97.7% test set accuracy**

[→ View Project](https://github.com/manojarulmurugan/Credit-Profit-Risk-Analysis)

---

### 🧩 Fall Detection System
> *Deep Learning · Video Classification · Computer Vision*

- Built a real-time fall detection system processing **46GB of video data** using **Convolutional LSTM** and **Long-term Recurrent Convolutional Network (LRCN)** architectures
- Engineered to handle temporal dependencies across video frames for reliable action recognition

**📊 82% test set accuracy**

[→ View Project](https://github.com/manojarulmurugan/Fall-Detection)

---

## 🔧 Work in Progress

### 🛒 E-Commerce Recommendation System *(active)*
> *BigData · GCP · MLOps*

Building a production-grade recommendation pipeline on a **70GB+ data lake** using GCS Storage, BigQuery, and Spark on Dataproc, with **MLFlow** for experiment tracking and model registry. Designed around real BigData constraints, not a toy dataset.

---

### 🗺️ SquadPlanner v2 *(active)*
> *Agentic AI · MCP · Google Maps API*

Expanding the original trip planner with **Google Maps integration**, broader location coverage, improved UI, and new **MCP + API integrations**, pushing toward a more robust agentic architecture.

---

## 📖 Currently Learning

| Course / Resource | Focus |
|---|---|
| *Principles of Designing AI Agents* by Sam Bhagwat | Agentic architectures, MCP servers, tool design |
| *Machine Learning in Production* by DeepLearning.ai | MLOps, model monitoring, cloud deployment |

✅ **Completed:** Deep Learning Specialization (DeepLearning.ai)

---

## 🛠️ Stack

**Core Languages**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![R](https://img.shields.io/badge/R-276DC3?style=flat-square&logo=r&logoColor=white)

**ML / Deep Learning**

![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=flat-square&logo=tensorflow&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-337AB7?style=flat-square&logoColor=white)
![HuggingFace](https://img.shields.io/badge/HuggingFace-FFD21E?style=flat-square&logo=huggingface&logoColor=black)

**LLM / Agentic AI**

![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat-square&logo=langchain&logoColor=white)
![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=flat-square&logo=openai&logoColor=white)

**Data & Infra**

![Snowflake](https://img.shields.io/badge/Snowflake-29B5E8?style=flat-square&logo=snowflake&logoColor=white)
![GCP](https://img.shields.io/badge/GCP-4285F4?style=flat-square&logo=googlecloud&logoColor=white)
![BigQuery](https://img.shields.io/badge/BigQuery-669DF6?style=flat-square&logo=googlebigquery&logoColor=white)
![MLflow](https://img.shields.io/badge/MLflow-0194E2?style=flat-square&logo=mlflow&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![PowerBI](https://img.shields.io/badge/PowerBI-F2C811?style=flat-square&logo=powerbi&logoColor=black)

---

## ⚡ Beyond the Code

When I'm not building something, I'm following football, the NBA, or cricket more closely than I probably should, or out running to balance it all out.

---

## 📄 Publication

**An Efficient Vehicle Detection and Shadow Removal Using Gaussian Mixture Models with Blob Analysis for Machine Vision Application**
*Computer vision research on vehicle detection in challenging lighting conditions*

---

## 📊 GitHub Stats

<div align="center">

<img src="https://streak-stats.demolab.com?user=manojarulmurugan&theme=tokyonight&hide_border=true" height="165"/>
&nbsp;
<img src="https://github-profile-summary-cards.vercel.app/api/cards/repos-per-language?username=manojarulmurugan&theme=tokyonight" height="165"/>

</div>

---

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0575E6,100:00c6ff&height=80&section=footer" />

</div>
