(Model, data, information coming soon -- containerizing for reproducibility, working on CI/CD workflow, LFS, and HuggingFace

## 1. Problem Definition

This project uses NVIDIA Merlin to build a scalable, GPU-accelerated recommender system based on **implicit feedback** (user play counts) from the [Million Song Dataset](https://labrosa.ee.columbia.edu/millionsong/).

### 🎯 Goal

Recommend the **Top-N songs** for each user based on their past listening behavior — no ratings, no pressure. Just music they’re likely to enjoy, based on what they actually listened to.

---

### 📌 Problem Type

- **Type:** Implicit Feedback Recommendation
- **Input:** User ID (and optionally metadata like listening frequency, genre)
- **Output:** Top-N recommended songs (can later generalize to artists)
- **Model Architecture:** Starting with a **Two-Tower model** using NVIDIA Merlin
- **Metric:** Precision@K, Recall@K, NDCG

---

### 🧠 Why Implicit Feedback?

Unlike explicit feedback (ratings), implicit signals like play counts offer a **natural and scalable** way to infer user preferences. This allows us to:
- Avoid popularity bias from 5-star ratings
- Reflect passive user behavior (the music they actually listen to)
- Create **personalized**, behavior-driven recommendations

---

### 📦 Dataset

We'll be using the **Taste Profile Subset** of the Million Song Dataset:
- Includes play counts (user–track pairs)
- ~1 million users, 384,000 songs
- Rich, large-scale data for training real-world recommenders

Download link (manual):
https://www.kaggle.com/datasets/msdlyrics/taste-profile-subset

Once retrieved, you can place the raw data under:
```bash
data/raw/taste_profile/
