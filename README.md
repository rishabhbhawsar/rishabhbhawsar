<!--
  NOTE: Verify the repository URLs marked "verify" before publishing.
  The two Live links come from your resume; repo paths follow your GitHub naming pattern.
-->

<div align="center">

# Rishabh Bhawsar

**Software & Machine Learning Engineer**
Backend Architecture · Data Contracts · Production ML Systems

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/rishabh-bhawsar-409098262/)
[![Email](https://img.shields.io/badge/Email-D14836?style=flat-square&logo=gmail&logoColor=white)](mailto:rishabhbhawsar53@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/rishabhbhawsar)
![Location](https://img.shields.io/badge/Based_in-Indore,_India-24292F?style=flat-square)

</div>

---

## Profile

B.E. in Artificial Intelligence & Data Science (University of Mumbai, 2026). I build systems that make probabilistic models behave like dependable services: strict data contracts, async pipelines, leakage-safe ML, and monitoring that catches failures before users do.

| Focus | Approach |
|:--|:--|
| **Applied GenAI** | LLM-as-a-Judge evaluation, schema-validated outputs, defensive failure handling |
| **Time-Series ML** | Leakage-safe features, forward-chaining validation, drift monitoring |
| **Backend Engineering** | FastAPI, Pydantic V2, asyncio concurrency, content-addressed caching |
| **Delivery** | CI-minded testing, reproducible metrics, live deployed demos |

---

## Production Systems Spotlights

### 01 · Async LLM-as-a-Judge Regulatory Compliance Gateway

> Evaluates unstructured business listings against market-specific KYC taxonomy rules and returns schema-validated verdicts.

[![Live Console](https://img.shields.io/badge/Live_UI_Console-Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white)](https://icp-policy-evaluator.vercel.app/)
[![Backend Source](https://img.shields.io/badge/Backend_Source-GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/rishabhbhawsar/icp-policy-evaluator)

![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![Pydantic](https://img.shields.io/badge/Pydantic_V2-E92063?style=flat-square&logo=pydantic&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite_WAL-003B57?style=flat-square&logo=sqlite&logoColor=white)
![OpenAI](https://img.shields.io/badge/OpenAI_SDK-412991?style=flat-square&logo=openai&logoColor=white)
![asyncio](https://img.shields.io/badge/asyncio-3776AB?style=flat-square&logo=python&logoColor=white)

| Layer | Engineering Detail |
|:--|:--|
| **Data Contracts** | Pydantic V2 models validate every request and every model response. Output that violates the schema is rejected at the gate and never returned as a verdict. |
| **Async Caching** | Content-hashed cache keys in asynchronous SQLite running in Write-Ahead Logging (WAL) mode. Repeated evaluations skip the network call, cutting redundant LLM cost and latency. |
| **Concurrency Control** | `asyncio.Semaphore` bounds in-flight API requests so throughput scales without tripping upstream rate limits. |
| **Defensive Exception Framework** | A local 6-mode failure taxonomy with Tenacity exponential backoff and jitter. Each failure class (for example JSON schema violation or token truncation) gets its own retry or fail-fast policy. |
| **Offline Batch Harness** | A custom parallel evaluation harness runs a hand-labeled benchmark suite (compliant, non-compliant, and ambiguous edge cases) with no manual review step. |

**Empirical findings, reported as measured**

| Metric | Observed Result |
|:--|:--|
| Classification outcome | **100%** success across the **7 core labeled sample cases** |
| Upstream reliability | **~38% transient failure rate** from free-tier model routing (non-deterministic) |
| Engineering takeaway | Model output volatility is a systems problem, not a prompt problem. That is why schema validation, error gating, and structured retries sit in front of every verdict. |

The 100% figure is measured on a small labeled suite and describes correctness after the defensive layer. It does not claim the underlying model is deterministic.

---

### 02 · Multi-Tenant Predictive Mainframe CPU Forecaster & MLOps Pipeline

> Forecasts hourly enterprise mainframe CPU utilization across a hierarchical topology and monitors live data drift.

[![Live Dashboard](https://img.shields.io/badge/Live_MLOps_Dashboard-Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white)](https://mainframe-cpu-forecaster.vercel.app/)
[![Source Code](https://img.shields.io/badge/Source_Code-GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/rishabhbhawsar/mainframe-cpu-forecaster)

![XGBoost](https://img.shields.io/badge/XGBoost-EC6B23?style=flat-square)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)
![SciPy](https://img.shields.io/badge/SciPy-8CAAE6?style=flat-square&logo=scipy&logoColor=white)
![joblib](https://img.shields.io/badge/joblib-parallel-4B5563?style=flat-square)
![Render](https://img.shields.io/badge/Render-46E3B7?style=flat-square&logo=render&logoColor=black)

| Layer | Engineering Detail |
|:--|:--|
| **Topology-Aware Modeling** | Ensemble XGBoost models structured along corporate boundaries: **Box → System → Service Class**. |
| **Leakage-Safe Features** | Temporal lags, rolling statistical summaries, and cyclical calendar encodings, all built to prevent lookahead bias. |
| **Validation Strategy** | Expanding-window, forward-chaining cross-splits, trained in parallel with joblib. An automated quality gate blocks noise-dominated channels from production export. |
| **Test Framework** | An automated **52-check** harness covering leakage probes, error-contract mapping, and live drift response. |
| **Drift Telemetry** | The live dashboard calculates vectorized **Population Stability Index (PSI)** and **two-sample Kolmogorov–Smirnov** tests. A shift is flagged at `p-value < 0.05`. |

**Verifiable calibration** (reproducible via `calculate_metrics.py`)

| Metric | Result |
|:--|:--:|
| Pooled out-of-fold MAE | **1.56%** |
| Pooled out-of-fold RMSE | **1.97%** |
| Train-serve parity skew | **0.000000** (floating-point) |
| Drift detection under injected regime shift | **11 / 11** monitored features flagged |

---

## Core System Capabilities & Toolchains

| Distributed Backend Frameworks | |
|:--|:--|
| **Runtime & Services** | Python · FastAPI · Asyncio · Pydantic V2 |
| **Reliability Patterns** | Semaphore concurrency control · Tenacity backoff and jitter · Content-hash caching |
| **Data Layer** | SQLite (WAL) · MongoDB · SQL |

| Machine Learning Infrastructure | |
|:--|:--|
| **Modeling** | XGBoost · Random Forest · Scikit-Learn · PyTorch · TensorFlow |
| **Time-Series & Validation** | Forward-chaining validation · Temporal feature engineering · Leakage probes |
| **Monitoring** | PSI · Kolmogorov–Smirnov test · SciPy |
| **GenAI & NLP** | LLM-as-a-Judge · RAG · Prompt Engineering · OpenAI SDK · LangChain · LangGraph · Transformers |

| Client UI Presentation Interfaces | |
|:--|:--|
| **Front-End** | HTML5 · CSS3 · JavaScript |
| **Hosting** | Vercel (UI consoles and dashboards) · Render (inference gateways) |

| Version Control & MLOps Systems | |
|:--|:--|
| **Source Control** | Git · GitHub |
| **Containers & Orchestration** | Docker · Kubernetes |
| **Delivery** | CI/CD · Automated test harnesses · Reproducible metric scripts · joblib model artifacts |

---

## Algorithmic Foundations

| Repository | Scope |
|:--|:--|
| [Leetcode-DSA-Submissions](https://github.com/rishabhbhawsar/Leetcode-DSA-Submissions) | Dynamic programming, graph algorithms, and advanced data structures in Java, with documented time and space complexity. |
| [algorithmxlr8-submission-2026-07-27](https://github.com/rishabhbhawsar/algorithmxlr8-submission-2026-07-27) | Competitive programming and assessment submissions from the algorithmxlr8 platform. |

---

## Education & Certifications

| | |
|:--|:--|
| **B.E., Artificial Intelligence & Data Science** | Datta Meghe College of Engineering, University of Mumbai · 2022 – 2026 |
| **Discrete Structures, Data Structures and Algorithms** | Udemy · Dec 2024 |
| **Version Control with Git** | Coursera · Jan 2025 |

---

<div align="center">

**Open to Software Engineering and Machine Learning Engineering roles.**

[LinkedIn](https://www.linkedin.com/in/rishabh-bhawsar-409098262/) · [Email](mailto:rishabhbhawsar53@gmail.com) · [GitHub](https://github.com/rishabhbhawsar)

</div>
