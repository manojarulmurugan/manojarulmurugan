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

> Graduated with my MS this May. Actively looking for full-time roles in **Data Science, ML Engineering, or Applied AI**.

**Currently exploring:** Going deeper on LLM fine-tuning with LoRA and QLoRA, and following up on a healthcare-data trust layer I built solo in a 16-hour Databricks × Hack-Nation hackathon (see below).

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
| [SpecDec-meets-Quant](#specdec-meets-quant) | Do stacked LLM inference optimizations actually compound in vLLM? | **2.97x** interference gap; found & reported a vLLM crash bug |
| [Healthcare Referral Copilot](#healthcare-referral-copilot) | Evidence-grounded facility search over India's messy healthcare data | 10,077 facilities, 451k evidence bullets, live on Databricks |
| [Time-Aware RAG](#time-aware-rag) | Temporal retrieval pipeline for "as-of" QA | **Hit@1: 59% vs 40.4% baseline** |
| [Hallucination Steering](#hallucination-aware-steering) | LLM truthfulness via hidden-state steering | **Hallucination rate: 64.6% → 55.5%** |
| [SquadPlanner](#squadplanner) | Stateful multi-agent trip planner with LangGraph | Live + deployed |
| [RecoSys](#recosys) | Production-scale session-based recommender on GCP | **NDCG@20 = 0.2676, +5.1% vs XLNet** |
| [Customer Churn & Retention Analytics](#customer-churn--retention-analytics) | XGBoost churn classification + retention analytics on 370k sales records | **87% accuracy, 0.89 precision** |
| [Credit Profit & Risk Analysis](#credit-profit--risk-analysis) | Investor portfolio selection vs LendingClub grading | **+200–460 bp annualized return** |

---

### SpecDec-meets-Quant
> *LLM Serving · Speculative Decoding · Quantization · GPU Optimization*

**[View Project](https://github.com/manojarulmurugan/SpecDecoding-Study-vLLM-SGLang)**

Practitioner guidance says weight quantization, KV-cache quantization, and speculative decoding stack into cleanly compounding serving speedups. This project tested that inside vLLM, under continuous batching and realistic concurrency, with a replicated 2³ factorial across 397 serving runs (Llama-3.1-8B, A100) — gated on first reproducing a published single-stream result before trusting any new measurement.

- **They don't compound.** Full-stack speedup trails the naive product of the three levers by up to **2.97×**, and every pairwise interaction is negative across all 12 workload × concurrency cells. The worst cell (GSM8K, concurrency 64) runs *slower* than no optimization at all.
- **Quality costs add cleanly, unlike speed.** AWQ quantization costs -3 to -8 accuracy points; FP8 KV-cache is ~0; EAGLE-3 under greedy decoding is bit-identical.
- **FP8-KV is a capacity lever, not a speed lever.** At KV-capacity pressure it doubles the admitted request batch, lifting goodput **+19%** and cutting P95 latency **-21%**.
- **Found, root-caused to file:line, and reported a real vLLM 0.24.0 bug**: a stale EAGLE-3 checkpoint field crashes compiled-mode long-context serving; diagnosed via per-position GPU instrumentation ([vllm#48894](https://github.com/vllm-project/vllm/issues/48894), open).
- Shipped a reusable, engine-agnostic benchmark harness (resumable sweeps, process-group-safe vLLM V1 lifecycle, GPU-free test suite) and a provenance-backed [deployment decision guide](https://github.com/manojarulmurugan/SpecDecoding-Study-vLLM-SGLang/blob/main/DECISION_GUIDE.md), where every number traces to a committed per-run record.

---

### Healthcare Referral Copilot
> *Full-Stack AI · Data Trust & Verification · Databricks*

**[Live Demo](https://data-legend-app-7474656737321234.aws.databricksapps.com) · [View Project](https://github.com/manojarulmurugan/hacknation-referral-copilot)**

Built solo in a 16-hour hackathon (Databricks × Hack-Nation "Data Legend" challenge, San Francisco). Care coordinators searching India's fragmented healthcare-facility data can't easily tell a verified capability from an unverified claim — "this hospital has an ICU" is often just text, not evidence. This app fixes that.

- **5-stage deterministic pipeline** turns 451k noisy free-text claims across 10,077 real facilities into scored, evidence-backed capability data, mapped against a 20-capability taxonomy grounded in WHO SARA + India IPHS 2022 standards
- **Rejected an LLM-based extraction approach after it failed at scale** (445 of 662 batches errored, covering only 528 of 10,077 facilities) in favor of a deterministic, 100%-coverage rule-based mapper
- **The LLM never originates a fact**: used only for query-parsing fallback and optional external corroboration, where any quote not verbatim in the retrieved source text is rejected outright
- Two rounds of external second-opinion code review caught and fixed real bugs in the trust-scoring logic before shipping — an "independent corroboration" rule that wasn't actually independent, and a contradiction-flag statistic that had the wrong denominator
- **Full-stack and deployed**: composite evidence + geography ranking, Postgres persistence via Databricks Lakebase (OAuth-secured, survives app restarts/redeploys), live on Databricks Apps with Llama-3-3-70B via Databricks Model Serving

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

**[Live Demo](https://ai-squad-planner-v2-0.vercel.app/) · [View Project](https://github.com/manojarulmurugan/AI-Squad-Planner-v2.0)**

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
- **FastAPI + FAISS serving on Hugging Face Spaces** (migrated from Cloud Run); profiled the serving path and cut FAISS search latency **11.5×** with an IVFFlat-512 index (94.9% concordance vs. brute-force), and validated dynamic request batching (**8× throughput** at high concurrency)
- **Weekly re-training pipeline**: JSD drift detection, experience replay, and rolling evaluation, stress-tested through the March 2020 COVID demand shock — best checkpoint lifted NDCG@20 to 0.2714 (+4.7%)
- **MLflow** experiment tracking (DagsHub); live distribution drift monitor (Jensen-Shannon divergence)
- SASRec attempted 5 times; all failed on short-session data. Documented as a negative result with literature backing

| Metric | GRU4Rec V9 | T4Rec XLNet (published) | Popularity baseline |
|---|---|---|---|
| NDCG@20 | **0.2676** | 0.2546 | 0.0353 |
| HR@20 | **0.4815** | 0.44 | 0.0806 |

---

### Customer Churn & Retention Analytics
> *Classification · Time-Series · Business Analytics*

**[View Project](https://github.com/manojarulmurugan/Customer-Churn-Prediction-Sales-Data)**

Churn prediction on 370,000 non-contractual sales transactions from a printing company, where there's no cancellation event to learn from. Forecasting-based and percentile-heuristic churn signals both turn out to be too weak — the project shows why, builds a supervised classifier that works, and connects it to segmentation and CLV for retention prioritization.

- ARIMA/LSTM revenue-forecasting churn flags and ECDF revenue-percentile heuristics both underperform (~50% and ~28% accuracy) — documented as weak baselines rather than used as the labeling method
- **XGBoost churn classifier: 87% accuracy, 0.89 precision, 0.90 recall**, built on recency/frequency, purchase-consistency, product, and geography features
- Segmentation and customer lifetime value (CLV) analysis layered on top to prioritize retention spend by risk × value

---

### Credit Profit & Risk Analysis
> *Machine Learning · Ensemble Methods · Fintech*

**[Live Demo](https://loan-alpha.streamlit.app/) · [View Project](https://github.com/manojarulmurugan/Credit-Profit-Risk-Analysis)**

Reframed from the standard lender accept/reject framing — which hits a structural ceiling since LendingClub already prices default risk into the interest rate — to investor portfolio selection: rank loans by predicted annualized net return rather than predicted default, and measure realized portfolio return.

- Beats LendingClub's own grade ordering by **200–460 bp in annualized portfolio return**, validated across four independent out-of-time cohorts (2012–2015), two of them at 100% loan maturity
- Model stack: XGBoost PD model (AUC 0.712) → LightGBM LGD model → LightGBM-Huber annualized-return model (trained on matured loans only) → discrete-time survival model for IFRS 9 lifetime PD/ECL → portfolio engine
- Grade-blind and leakage-guarded: `int_rate`/`sub_grade` excluded from features, cashflow columns used only as targets, strict out-of-time validation throughout
- Deployed as a FastAPI scoring endpoint + Streamlit investor dashboard

---

## Courses & Books

**Completed**

| Course / Book | Provider |
|---|---|
| Principles of Designing AI Agents | Sam Bhagwat |
| Neural Networks and Deep Learning | Dr. Andrew Ng |
| Improving Deep Neural Networks: Hyperparameter Tuning, Regularization and Optimization | Dr. Andrew Ng |
| Structuring Machine Learning Projects | Dr. Andrew Ng |
| Convolutional Neural Networks | Dr. Andrew Ng |
| Sequence Models | Dr. Andrew Ng |
| Machine Learning in Production | Dr. Andrew Ng |
| iOS & Swift - The Complete iOS App Development Bootcamp | Dr. Angela Yu |
| Data Structures and Algorithms Bootcamp | Jonathan Rasmusson |

**Currently studying**

| Course / Book | Author |
|---|---|
| Inference Engineering | Philip Kiely |
| Ace the Data Science Interview | Nick Singh and Kevin Huo |

---

## Stack

**Core Languages**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![R](https://img.shields.io/badge/R-276DC3?style=flat-square&logo=r&logoColor=white)
![Julia](https://img.shields.io/badge/Julia-9558B2?style=flat-square&logo=julia&logoColor=white)

**ML / Deep Learning**

![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-337AB7?style=flat-square&logoColor=white)
![LightGBM](https://img.shields.io/badge/LightGBM-02569B?style=flat-square&logoColor=white)
![HuggingFace](https://img.shields.io/badge/HuggingFace-FFD21E?style=flat-square&logo=huggingface&logoColor=black)

**LLM / Agentic AI & Serving**

![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat-square&logo=langchain&logoColor=white)
![LangGraph](https://img.shields.io/badge/LangGraph-1C3C3C?style=flat-square&logoColor=white)
![vLLM](https://img.shields.io/badge/vLLM-000000?style=flat-square&logoColor=white)
![FAISS](https://img.shields.io/badge/FAISS-4285F4?style=flat-square&logoColor=white)

**Data & Cloud Infra**

![GCP](https://img.shields.io/badge/GCP-4285F4?style=flat-square&logo=googlecloud&logoColor=white)
![BigQuery](https://img.shields.io/badge/BigQuery-669DF6?style=flat-square&logo=googlebigquery&logoColor=white)
![Snowflake](https://img.shields.io/badge/Snowflake-29B5E8?style=flat-square&logo=snowflake&logoColor=white)
![Databricks](https://img.shields.io/badge/Databricks-FF3621?style=flat-square&logo=databricks&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat-square&logo=mongodb&logoColor=white)
![Apache Spark](https://img.shields.io/badge/Apache%20Spark-E25A1C?style=flat-square&logo=apachespark&logoColor=white)
![MLflow](https://img.shields.io/badge/MLflow-0194E2?style=flat-square&logo=mlflow&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![dbt](https://img.shields.io/badge/dbt-FF694B?style=flat-square&logo=dbt&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=flat-square&logo=streamlit&logoColor=white)

**Also use:** Pandas, NumPy, Polars, Darts, Vertex AI, Feature Stores, ETL, Tableau, PowerBI, Git, A/B & hypothesis testing

---

## Beyond the Code

Proud Tamil, from Chennai — if we ever meet, I'm taking you for masala dosa and filter coffee, no discussion. Sports are close to a religion: lifelong Messi/Barcelona fan still waiting on that Champions League, I bleed yellow for CSK, and I've recently gone deep into the NBA (Giannis and Wemby) and started following F1 and tennis. I play football myself whenever I can — box-to-box midfielder, chaos included — plus distance running, pickleball, and badminton, all played with more competitiveness than is probably healthy.

Off the field: a huge Christopher Nolan fan, currently on both the *One Piece* anime and manga, and I read way more history and geopolitics than the average data scientist for fun — the patterns across civilizations aren't that different from how I think about data.

---

## Publication

**[An Efficient Vehicle Detection and Shadow Removal Using Gaussian Mixture Models with Blob Analysis for Machine Vision Application](https://www.researchgate.net/publication/371638299_An_Efficient_Vehicle_Detection_and_Shadow_Removal_Using_Gaussian_Mixture_Models_with_Blob_Analysis_for_Machine_Vision_Application)**
*SN Computer Science, 2023*

Detects and counts vehicles from CCTV footage: morphological filtering removes noise, blob analysis + Gaussian Mixture Models detect and count vehicles per frame, benchmarked against YOLO.

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
