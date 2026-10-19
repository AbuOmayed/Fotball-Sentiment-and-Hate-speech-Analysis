# BFFSH-Dataset: Sentiment Analysis and Hate Speech Detection of Bangladeshi Football Fans’ Comments

[![Paper](https://img.shields.io/badge/Paper-IEEE-blue.svg)](#) <!-- Add link to paper when published -->
[![Dataset](https://img.shields.io/badge/Dataset-BFFSH-orange.svg)](#) 

This repository contains the official dataset, preprocessing scripts, and deep learning models for the paper: **"BFFSH-dataset: A Dataset for Sentiment Analysis and Hate Speech Detection of Bangladeshi Football Fans’ Comments on the FIFA World Cup 2026."**

## 📖 Overview
Football discussions on social media are highly expressive, combining enthusiastic support with instances of extreme frustration and hate speech. This project tackles the challenge of analyzing this discourse in a low-resource language (Bengali/Bangla). 

We introduce the **BFFSH-Dataset**, a dual-annotated dataset comprising **11,565** comments from Bangladeshi football fans during the FIFA World Cup 2026. The repository provides baseline and hybrid deep learning architectures to perform two distinct NLP tasks simultaneously:
1. **Sentiment Analysis** (Positive, Negative, Neutral)
2. **Hate Speech Detection** (Hate, Normal)

## 📊 The BFFSH-Dataset
The dataset was curated from Facebook (70%) and YouTube (30%) and dual-annotated by NLP experts and graduate students via majority voting. 

### Class Distribution
| Platform | Total Comments | Sentiment (Pos / Neg / Neu) | Hate Speech (Hate / Normal) |
| :--- | :--- | :--- | :--- |
| **Facebook** | 8,096 | 2,011 / 4,725 / 1,360 | 4,696 / 3,399 |
| **YouTube** | 3,469 | 1,112 / 2,052 / 305 | 2,012 / 1,458 |
| **Total** | **11,565** | **3,123 / 6,777 / 1,665** | **6,708 / 4,857** |

*(Note: The dataset is available upon request to the primary author. Please see the contact details in the paper).*

## 🧠 Methodology

### Data Preprocessing & Feature Extraction
* **Regex Cleaning:** Removal of HTML, hyperlinks, and cross-lingual noise (Latin alphabets `[a-zA-Z]`).
* **Numeric Filtering:** Removal of ASCII `[0-9]` and Bengali `[০-৯]` digits.
* **Unicode Masking:** Strict filtering to `[\u0980-\u09FF\s]` to preserve only legitimate Bengali characters, stripping emojis and punctuation.
* **Feature Extraction:** TF-IDF vectorization to capture relative token significance.

### Evaluated Architectures
We evaluated 6 deep learning architectures, including a novel proposed triple-hybrid model:
* **Baselines:** 1D-CNN, LSTM, GRU
* **Hybrid Models:** 1D-CNN-LSTM, 1D-CNN-GRU
* **Proposed Model:** **1D-CNN-LSTM-GRU** (Captures local spatial features via CNN, distant contextual dependencies via LSTM, and temporal dynamics via GRU).

## 🏆 Key Results

### Task 1: Sentiment Analysis
The proposed **1D-CNN-LSTM-GRU** model achieved highly competitive results, offering balanced classification alongside the LSTM baseline.

| Model | Accuracy | Recall | F1-Score | ROC-AUC |
| :--- | :--- | :--- | :--- | :--- |
| 1D-CNN | 0.79 | 0.73 | 0.74 | **0.94** |
| LSTM | 0.80 | 0.74 | **0.75** | 0.92 |
| GRU | 0.79 | 0.73 | 0.74 | 0.92 |
| 1D-CNN-LSTM | 0.59 | 0.39 | 0.37 | 0.72 |
| 1D-CNN-GRU | 0.67 | 0.57 | 0.57 | 0.82 |
| **1D-CNN-LSTM-GRU (Ours)** | **0.82** | **0.72** | 0.74 | 0.92 |

### Task 2: Hate Speech Detection
For hate speech detection, the proposed **1D-CNN-LSTM-GRU** architecture successfully optimized the recall for hateful content (0.87), making it highly sensitive to toxic behavior compared to the baselines.

| Model | Accuracy | F1-Score | ROC-AUC |
| :--- | :--- | :--- | :--- |
| 1D-CNN | 0.80 | 0.78 | **0.90** |
| LSTM | 0.80 | 0.79 | 0.90 |
| GRU | 0.80 | 0.79 | 0.89 |
| 1D-CNN-LSTM | 0.72 | 0.72 | 0.81 |
| 1D-CNN-GRU | 0.41 | 0.29 | 0.36 |
| **1D-CNN-LSTM-GRU (Ours)**| **0.81** | **0.80** | 0.89 |

## 🚀 Getting Started

### Prerequisites
* Python 3.8+
* TensorFlow / Keras 2.x
* Scikit-learn
* Pandas & NumPy

### Installation
1. Clone the repository:
   ```bash
   git clone [https://github.com/your-username/BFFSH-Dataset-Analysis.git](https://github.com/your-username/BFFSH-Dataset-Analysis.git)
   cd BFFSH-Dataset-Analysis
