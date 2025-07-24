# 🎵 TuneTower: Scalable Music Recommendations with Spark, NVIDIA Merlin & Triton Inference

> A production-grade hybrid recommender system using Spark ALS, NVIDIA Merlin Two-Tower architecture, and Triton Server for real-time music personalization.

---

## 🧠 Overview

**TuneTower** is an end-to-end, modular recommender system that combines:
- **Distributed matrix factorization (ALS)** for scalable collaborative filtering
- **Deep neural retrieval (Two-Tower)** using **NVIDIA Merlin**
- **GPU-accelerated preprocessing** with NVTabular
- **Low-latency inference** using **Triton Inference Server**
- **Full CI/CD orchestration** with GitHub Actions + MLflow model tracking

The project is built on the **Million Song Dataset** and designed to demonstrate real-world MLE and MLOps workflows for large-scale recommendation engines.

---

## 📐 Architecture

```mermaid
flowchart TD
    %% Data pipeline
    A[Million Song Dataset] --> B[Apache Spark: ALS + Metadata]
    B --> C[NVTabular Preprocessing]

    %% Modeling
    C --> D[Two-Tower Model (Merlin)]
    D --> E[FAISS / ScaNN Index]
    D --> F[Reranker (LightGBM / DIN)]

    %% Serving
    E --> G[Triton Inference Server]
    F --> G
    G --> H[FastAPI Wrapper]

    %% MLOps
    D --> I[MLflow Registry]
    C --> J[CI/CD - GitHub Actions]
```

---

## 🗃️ Dataset

**Million Song Dataset**  
- 1M tracks with artist, title, year, and metadata  
- Extended with Last.fm user play count data  
- Format: HDF5, CSV, Parquet  
- Preprocessing includes filtering, bucketing, genre encoding

📦 [https://labrosa.ee.columbia.edu/millionsong/](https://labrosa.ee.columbia.edu/millionsong/)

---

## 🔧 Tech Stack

| Layer | Tools Used |
|-------|------------|
| **Data** | Apache Spark, NVTabular |
| **Modeling** | Spark ALS, Merlin Two-Tower, FAISS, LightGBM |
| **Serving** | NVIDIA Triton Inference Server, FastAPI |
| **Tracking** | MLflow |
| **CI/CD** | GitHub Actions |
| **Monitoring (Planned)** | Prometheus, Evidently AI |

---

## 📈 Evaluation Metrics

- **Recall@K**, **MAP@K**, **NDCG@K** for retrieval phase
- **Hit Rate**, **AUC**, **MRR** for reranking
- Offline logs tracked via MLflow

---

## 🚀 Project Goals

- ✅ Scalable retrieval system using matrix factorization (Spark ALS)
- ✅ Deep learning-based personalization using Two-Tower network with Merlin
- ✅ Real-time serving with Triton and ANN indexing
- ✅ CI/CD pipeline for retraining, testing, and deployment
- ⏳ Drift detection, auto-retraining, and A/B testing support (future)

---

## 🧪 Getting Started

```bash
# Clone the repo
git clone https://github.com/yourname/tunetower.git
cd tunetower

# (Optional) Set up environment
conda env create -f environment.yml
conda activate tunetower

# Run ALS pipeline
spark-submit spark_jobs/train_als.py

# Run NVTabular pipeline
python merlin_models/preprocess.py
```

---

## 📂 Folder Guide

```
tunetower/
├── data/                 # Raw and processed data (DVC-tracked)
├── spark_jobs/           # ALS training, feature extraction
├── merlin_models/        # NVTabular + Two-Tower deep retrieval
├── serving/              # Triton server config + FastAPI wrapper
├── mlflow/               # Experiment tracking scripts
├── .github/workflows/    # CI/CD jobs (train, test, deploy)
├── tests/                # Pytest + Great Expectations
└── README.md             # This file
```

---

## 🛠️ Roadmap

- [x] Spark-based ALS retrieval system
- [x] GPU-based NVTabular preprocessing
- [x] Deep Two-Tower recommendation with NVIDIA Merlin
- [ ] Real-time inference via Triton + ANN index
- [ ] Model monitoring & data drift detection
- [ ] Feature store integration (Feast or custom)
- [ ] Streamlit or UI interface

---

## 📄 License

MIT License

---

## 🙋‍♂️ Author

**Steven Haworth**  
_Machine Learning Engineer | Scalable Systems & Recommender Architectures_  
📫 [LinkedIn](https://www.linkedin.com/in/your-link) · 💻 [GitHub](https://github.com/your-github)

---

## ⭐️ Give this project a star if you like recommender systems + GPUs!
d
