<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0575E6,100:00c6ff&height=130&section=header&text=Manoj%20Arulmurugan&fontSize=38&fontColor=ffffff&fontAlignY=60&desc=Data%20Scientist%20%7C%20ML%20Engineer%20%7C%20UW-Madison%20%2726&descAlignY=80&descSize=15&descColor=dde8ff" />

### MS Data Science @ UW-Madison (May 2026) &nbsp;·&nbsp; Previously @ Calix & Shell India &nbsp;·&nbsp; Open to full-time roles

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/manojarulmurugan/)
[![Gmail](https://img.shields.io/badge/Gmail-manojarulmurugan@gmail.com-D14836?style=flat-square&logo=gmail&logoColor=white)](mailto:manojarulmurugan@gmail.com)
[![Portfolio](https://img.shields.io/badge/Portfolio-manojarulmurugan.vercel.app-000000?style=flat-square&logo=vercel&logoColor=white)](https://manojarulmurugan.vercel.app)

</div>

---

## About Me

ML and AI person at heart, with a foundation in production systems and an eye on where the field is heading.

Data makes real-world problems tangible to me. When I can see a problem through numbers, patterns, and structure, solving it becomes genuinely exciting, and that's what keeps pulling me deeper into this field.

I care about the full arc: from modeling to deployment, from classical ML to agentic systems and LLMs. I've shipped real ML systems in industry, worked across time-series, deep learning, and retrieval-based AI, and I'm actively building in MLOps, NLP, and agentic AI because that's where things are getting interesting.

> Finishing my MS this May. Actively looking for full-time roles in **Data Science, ML Engineering, or Applied AI**.

**Currently exploring:** LLM fine-tuning with LoRA and QLoRA, working on an early idea. Also going deeper on inference engineering and GPU optimization.

---

## Experience

### Machine Learning Intern @ Calix, Inc. *(Jun–Dec 2025 · San Jose, CA)*
- Architected a centralized **Feature Store on Snowflake** integrating **10+ data sources** and **100+ engineered features**
- Redesigned the production Account-Level Regression model into **13 week-specific models** with algorithm-specific feature selection (VIF + Genetic Algorithm for linear; SHAP for tree), achieving **~50% MAPE reduction**
- Productionized full pipeline on Snowflake-dbt, reducing dimensionality by **~80%** through Genetic Algorithm-based selection; optimized training window to meet a **30-minute warehouse timeout** and cut compute costs
- Contributed to the broader forecasting ensemble (SARIMA + LSTM + ALR) achieving **~60% overall accuracy improvement**

### Operations Data Analyst @ Shell India *(Aug 2023–Aug 2024 · Bangalore)*
- Owned operational analytics for B2C apps; built **PowerBI dashboards** on a **10TB data lake** via SQL, driving **$250,000 in cost savings**
- Engineered automated **ETL pipelines**, accelerating data processing **3x**
- **Shell Mobility Wall of Fame Award, Q1 2024**

---

## Projects

| Project | What it does | Key Result |
|---|---|---|
| [Time-Aware RAG](#time-aware-rag) | Temporal retrieval pipeline for "as-of" QA | **Hit@1: 59% vs 40.4% baseline** |
| [Hallucination Steering](#hallucination-aware-steering) | LLM truthfulness via hidden-state steering | **Hallucination rate: 64.6% → 55.5%** |
| [SquadPlanner](#squadplanner) | Stateful multi-agent trip planner with LangGraph | Live + deployed |
| [RecoSys](#recosys) | Production-scale session-based recommender on GCP | **NDCG@20 = 0.2676, +5.1% vs XLNet** |
| [Sales Forecasting + Churn](#sales-forecasting--churn) | ARIMA/LSTM + LightGBM on 370k records | **<5% forecast error · 87% churn accuracy** |
| [Credit Risk Analysis](#credit-risk-analysis) | Stacked ensemble on 30k loan records | **97.7% accuracy** |

---

### Time-Aware RAG
> *Retrieval-Augmented Generation · NLP · Information Retrieval*

**[Live Demo](https://huggingface.co/spaces/manojarulmurugan/time-aware-rag) · [Fine-tuned Model](https://huggingface.co/manojarulmurugan/time-aware-contriever) · [View Project](https://github.com/manojarulmurugan/Time-Aware-Retrieval-Augmented-Generation)**

Standard dense retrievers find semantically similar passages regardless of *when* a fact was true. This one doesn't.

- Built a pipeline for **"as-of / when"** questions using year-anchored FineWeb-Edu Q-passage pairs (20k passages, T5 question generation)
- Fine-tuned **Contriever** with temporal hard negatives via triplet margin loss, mixed with 1k MS MARCO triplets to prevent forgetting general retrieval ability
- Built **MRAG re-ranker** using Sliding-Window MaxSim + temporal-decay fusion; window embeddings pre-computed at startup for fast inference
- Evaluated on **ChroniclingAmericaQA** (12,695 passages, year-explicit questions)

| Configuration | Hit@1 | MRR@10 |
|---|---|---|
| Base Contriever | 40.4% | 47.7% |
| Time-Aware + MRAG | **59.1%** | **65.7%** |

---

### Hallucination-Aware Steering
> *LLM Safety · Interpretability · Hallucination Mitigation*

**[View Project](https://github.com/manojarulmurugan/Probe-Controlled-TSV)**

- Trained a **Logistic Regression Truthfulness Separator Vector (TSV)** on GPT-Neo-2.7B hidden states, replacing centroid/OT steering
- Built a lightweight **MLP hallucination-risk probe** to adapt per-token steering strength, capped to prevent logit explosion
- Steered only **~57% of tokens**, preserving fluency while targeting high-risk positions

**TruthfulQA: 64.6% → 55.5% hallucination rate (+9.1pp)**

---

### SquadPlanner
> *LangGraph · Multi-Agent Systems · FastAPI · MongoDB*

**[Live Demo](https://ai-squad-planner-v2-0.vercel.app/) · [View Project](https://github.com/manojarulmurugan/AI-Squad-Planner)**

A stateful multi-agent trip planner for groups. The architecture was designed for efficiency: the entire planning pipeline runs on **only 3 LLM calls**, with parallel tool execution handling the rest.

- **LangGraph orchestrator** with MongoDB-backed checkpointing (`MongoDBCheckpointer`) for human-in-the-loop destination approval and stateful pause/resume across HTTP
- **Parallel fan-out** via `asyncio.gather` across 5 external APIs (flights, hotels, activities, weather, routes)
- **Stateful post-generation refinement**: natural-language edits ("Make Day 2 cheaper") re-enter the graph at the affected node via LangGraph checkpoint state, rerunning only the downstream subgraph
- **SSE streaming** for real-time agent progress; typed hard constraints parsed from free-text gate tool selection
- Deployed: **FastAPI + React (Vercel + Render)**

---

### RecoSys
> *Big Data · GCP · Session-Based Recommendations · MLOps*

**[Live Demo](https://recosys.vercel.app/) · [View Project](https://github.com/manojarulmurugan/RecoSys)**

End-to-end production recommendation system on the REES46 eCommerce dataset (288M raw events, Oct 2019–Jan 2020).

- **PySpark preprocessing** on GCP Dataproc: bot removal, exact + near-dedup, 3-core filtering across 279.9M events → 1.45M training sessions
- **GRU4Rec V9**: single-layer GRU with event-type embeddings, cosine similarity head (temperature = 0.07), full softmax over 222,864 items; trained on Vertex AI A100 (10h 46m)
- Scaling from 500k → 1M users produced a consistent **+2.7% NDCG@20** gain
- **FastAPI serving on Cloud Run** with FAISS ANN search (<500ms); automated concept-drift retraining via Cloud Scheduler + Vertex AI when rolling NDCG@20 drops >15%
- **MLflow** experiment tracking; live distribution drift monitor (Jensen-Shannon divergence)
- SASRec attempted 5 times; all failed on short-session data. Documented as a negative result with literature backing

| Metric | GRU4Rec V9 | T4Rec XLNet (published) | Popularity baseline |
|---|---|---|---|
| NDCG@20 | **0.2676** | 0.2546 | 0.0353 |
| HR@20 | **0.4815** | 0.44 | 0.0806 |

---

### Sales Forecasting + Customer Churn
> *Time-Series · Classification · Business Analytics*

**[View Project](https://github.com/manojarulmurugan/Sales-Forecasting-and-Customer-Segmentation-on-Sales-Data)**

- **ARIMA + LSTM** forecasting on a 370,000-record sales dataset with **<5% forecast error**
- ECDF-based dynamic churn labeling using per customer-product purchase-gap thresholds at the 90th percentile, capturing behavioral heterogeneity without fixed cutoffs
- **LightGBM + RandomForest** churn prediction at **87% accuracy**

---

### Credit Risk Analysis
> *Machine Learning · Ensemble Methods · Fintech*

**[View Project](https://github.com/manojarulmurugan/Credit-Profit-Risk-Analysis)**

- Stacked ensemble (RF + Naive Bayes + SVM + XGBoost) on 30,000 loan records with SMOTE and bootstrapping for class imbalance
- Profit optimization framing across risk tiers: actionable insights on safe loans and expected return by risk segment

**97.7% test set accuracy**

---

## Currently Learning

| Course / Resource | Focus |
|---|---|
| *Principles of Designing AI Agents* by Sam Bhagwat | Agentic architectures, MCP servers, tool design |
| *Machine Learning in Production* by DeepLearning.ai | MLOps, model monitoring, cloud deployment |

Completed: Deep Learning Specialization (DeepLearning.ai)

---

## Stack

**Core Languages**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![R](https://img.shields.io/badge/R-276DC3?style=flat-square&logo=r&logoColor=white)

**ML / Deep Learning**

![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-337AB7?style=flat-square&logoColor=white)
![HuggingFace](https://img.shields.io/badge/HuggingFace-FFD21E?style=flat-square&logo=huggingface&logoColor=black)

**LLM / Agentic AI**

![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat-square&logo=langchain&logoColor=white)
![LangGraph](https://img.shields.io/badge/LangGraph-1C3C3C?style=flat-square&logoColor=white)

**Data & Infra**

![Snowflake](https://img.shields.io/badge/Snowflake-29B5E8?style=flat-square&logo=snowflake&logoColor=white)
![GCP](https://img.shields.io/badge/GCP-4285F4?style=flat-square&logo=googlecloud&logoColor=white)
![BigQuery](https://img.shields.io/badge/BigQuery-669DF6?style=flat-square&logo=googlebigquery&logoColor=white)
![MLflow](https://img.shields.io/badge/MLflow-0194E2?style=flat-square&logo=mlflow&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![dbt](https://img.shields.io/badge/dbt-FF694B?style=flat-square&logo=dbt&logoColor=white)

---

## Beyond the Code

When I'm not building something, I'm following football, the NBA, or cricket more closely than I probably should, or out running to balance it all out.

---

## Publication

**An Efficient Vehicle Detection and Shadow Removal Using Gaussian Mixture Models with Blob Analysis for Machine Vision Application**
*Computer vision research on vehicle detection in challenging lighting conditions*

---

## GitHub Stats

<div align="center">

<img src="https://streak-stats.demolab.com?user=manojarulmurugan&theme=tokyonight&hide_border=true" height="165"/>
&nbsp;
<img src="https://github-profile-summary-cards.vercel.app/api/cards/repos-per-language?username=manojarulmurugan&theme=tokyonight" height="165"/>

</div>

---

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0575E6,100:00c6ff&height=80&section=footer" />

</div>
