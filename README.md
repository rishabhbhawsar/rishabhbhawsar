<div align="center">

# Rishabh Bhawsar

### Software & Machine Learning Engineer
Production ML systems · LLM evaluation · Async Python backends · MLOps

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/rishabh-bhawsar-409098262/)
[![Email](https://img.shields.io/badge/Email-D14836?style=flat-square&logo=gmail&logoColor=white)](mailto:rishabhbhawsar53@gmail.com)
![Location](https://img.shields.io/badge/Indore,_India-24292F?style=flat-square)
![Status](https://img.shields.io/badge/Open_to_work-SWE_%2F_ML_Engineer-2EA043?style=flat-square)

</div>

I build ML and LLM systems that behave like dependable services: strict data contracts, async pipelines, leakage-safe modeling, and monitoring that catches distributed failures early. Final-year AI & Data Science student, actively shipping production-style full-stack systems.

---

## Currently

- **Building:** AgentFlow — a multi-agent research assistant with LangGraph, MCP tool calling, Chroma, and a RAGAS-style evaluation harness.
- **Deepening:** MLOps practice with Docker, GitHub Actions, and cloud deployment.
- **Looking for:** Entry-level AI Engineer roles, remote or Bengaluru/Hyderabad/Mumbai.

---

## Selected Work

### LLM Compliance Gateway
*Async LLM-as-a-Judge regulatory compliance evaluation for business listings*

Evaluates business listings against market-specific KYC taxonomy rules and returns schema-validated verdicts.

[![Live Demo](https://img.shields.io/badge/Live_Demo-Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white)](https://icp-policy-evaluator.vercel.app/)
[![Source](https://img.shields.io/badge/Source_Code-GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/rishabhbhawsar/icp-policy-evaluator)

**Key results:** 28-case hand-labeled adversarial benchmark · Precision 1.00 · Recall 0.82 · 93% accuracy · 0 false positives across runs · ~21% transient upstream failure rate surfaced and contained by validation gating

`Python` `FastAPI` `Pydantic V2` `asyncio` `SQLite (WAL)` `Groq` `Tenacity`

- **Data contracts:** Pydantic V2 validates every request and every model response, including cross-field consistency between classification and risk level. Schema-violating output is rejected before it becomes a verdict.
- **Async caching:** content-hashed keys in asynchronous SQLite (WAL mode) skip repeat network calls — verified under test to bypass the judge entirely on a cache hit.
- **Defensive error handling:** a typed failure taxonomy (schema violations, token truncation, provider refusals, empty bodies) with Tenacity exponential backoff, jitter, and semaphore-based concurrency control.
- **Testing:** an automated benchmark harness runs 28 labeled cases spanning compliant, ambiguous, explicit-denial, surface-risk-but-compliant, prompt-injection, and public-company-exemption categories with no manual review step.
- **Adversarial robustness:** the judge resists prompt-injection and field-spoofing attempts without additional guardrails.
- **Engineering finding:** the benchmark exposed a ~21% transient upstream failure rate on the free tier, which is why schema validation and retries sit in front of every verdict.

---

### Mainframe CPU Forecaster
*Multi-tenant time-series forecasting with a live MLOps drift dashboard*

Forecasts hourly enterprise mainframe CPU utilization across a Box → System → Service Class hierarchy and monitors live data drift.

[![Live Demo](https://img.shields.io/badge/Live_Dashboard-Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white)](https://mainframe-cpu-forecaster.vercel.app/)
[![Source](https://img.shields.io/badge/Source_Code-GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/rishabhbhawsar/mainframe-cpu-forecaster)

**Key results:** 1.56% pooled MAE · 1.97% pooled RMSE (out-of-fold) · 11/11 drifted features flagged under an injected regime shift · 52-check automated test harness

`Python` `XGBoost` `FastAPI` `Scikit-Learn` `SciPy` `joblib` `Render`

- **Modeling:** ensemble XGBoost models structured along the corporate topology, with lag, rolling-window, and cyclical calendar features built to prevent lookahead bias.
- **Validation:** expanding-window forward-chaining splits with parallel training. An automated quality gate blocks noise-dominated channels from production export.
- **Reproducible accuracy:** pooled MAE and RMSE are computed by `calculate_metrics.py` on out-of-fold predictions.
- **Drift monitoring:** vectorized Population Stability Index and two-sample Kolmogorov–Smirnov tests, flagged at `p < 0.05`.
- **Reliability:** the 52-check harness covers leakage probes, error-contract mapping, and live drift response, and confirmed zero train-serve skew (0.000000 floating-point difference).

---

### Alert Clustering Engine
*Alert Clustering & Automated Notification System (NLP · Unsupervised ML)*

Reduces operational alert fatigue by clustering raw log streams and routing severity-based notifications with centroid context.

[![Source](https://img.shields.io/badge/Source_Code-GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/rishabhbhawsar/alert-clustering-engine)

`Python` `Scikit-Learn` `DBSCAN` `PCA` `LDA` `NumPy` `NLP` `Unsupervised ML`

- **Clustering:** stateless NLP alert clustering system that vectorizes raw operational logs using a Term-Frequency (TF) matrix and sliding-window DBSCAN density routing.
- **Dimensionality reduction:** Principal Component Analysis (PCA) maps alert coordinates onto an interactive 2D cluster canvas, with Latent Dirichlet Allocation (LDA) for cluster topic modeling.
- **Notification automation:** severity-based asynchronous notifications embedded with rich centroid context to accelerate operational incident triage workflows.

---

## Tech Stack

<p align="left">
  <a href="https://www.python.org" target="_blank"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="python" width="40" height="40"/></a>
  <a href="https://www.java.com" target="_blank"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/java/java-original.svg" alt="java" width="40" height="40"/></a>
  <a href="https://fastapi.tiangolo.com" target="_blank"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/fastapi/fastapi-original.svg" alt="fastapi" width="40" height="40"/></a>
  <a href="https://www.postgresql.org" target="_blank"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/postgresql/postgresql-original.svg" alt="postgresql" width="40" height="40"/></a>
  <a href="https://www.sqlite.org" target="_blank"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/sqlite/sqlite-original.svg" alt="sqlite" width="40" height="40"/></a>
  <a href="https://www.mongodb.com" target="_blank"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mongodb/mongodb-original.svg" alt="mongodb" width="40" height="40"/></a>
  <a href="https://www.docker.com" target="_blank"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/docker/docker-original.svg" alt="docker" width="40" height="40"/></a>
  <a href="https://git-scm.com" target="_blank"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/git/git-original.svg" alt="git" width="40" height="40"/></a>
  <a href="https://github.com" target="_blank"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/github/github-original.svg" alt="github" width="40" height="40"/></a>
  <a href="https://www.linux.org" target="_blank"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/linux/linux-original.svg" alt="linux" width="40" height="40"/></a>
  <a href="https://pytorch.org" target="_blank"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/pytorch/pytorch-original.svg" alt="pytorch" width="40" height="40"/></a>
  <a href="https://www.tensorflow.org" target="_blank"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/tensorflow/tensorflow-original.svg" alt="tensorflow" width="40" height="40"/></a>
  <a href="https://aws.amazon.com" target="_blank"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/amazonwebservices/amazonwebservices-original-wordmark.svg" alt="aws" width="40" height="40"/></a>
  <a href="https://code.visualstudio.com" target="_blank"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/vscode/vscode-original.svg" alt="vscode" width="40" height="40"/></a>
</p>

---

## Technical Skills

| Area | Tools |
|:--|:--|
| **Backend** | Python, Java, FastAPI, Asyncio, Pydantic, Tenacity, SQL, SQLite, PostgreSQL, MongoDB |
| **Machine Learning** | XGBoost, Scikit-Learn, PyTorch, TensorFlow, Pandas, NumPy, SciPy, joblib |
| **GenAI & NLP** | LLM-as-a-Judge, RAG, Prompt Engineering, OpenAI SDK, Groq, LangChain, LangGraph, Transformers |
| **MLOps & Tooling** | Git, GitHub, Docker, GitHub Actions, pytest, Vercel, Render, Linux |
| **Frontend** | HTML, CSS, JavaScript |

---

## Education

**B.E., Artificial Intelligence & Data Science**
Datta Meghe College of Engineering, University of Mumbai · 2022–2026

Algorithm practice in Java (dynamic programming, graphs, data structures): [Leetcode-DSA-Submissions](https://github.com/rishabhbhawsar/Leetcode-DSA-Submissions)

---

<div align="center">

![GitHub Stats](https://github-readme-stats.vercel.app/api?username=rishabhbhawsar&show_icons=true&theme=dark&hide_border=true&include_all_commits=true)

![Top Languages](https://github-readme-stats.vercel.app/api/top-langs/?username=rishabhbhawsar&layout=compact&theme=dark&hide_border=true)

**Open to Software Engineering and ML Engineering roles.** [Email](mailto:rishabhbhawsar53@gmail.com) · [LinkedIn](https://www.linkedin.com/in/rishabh-bhawsar-409098262/)

</div>
