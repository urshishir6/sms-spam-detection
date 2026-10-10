# A Transformer-Based Classification: A Case Study of Semantic Context Evaluation for Mobile Spam Message Detection

This repository contains the implementation, evaluation, and documentation for a comparative study on mobile SMS spam and phishing (smishing) detection[cite: 1, 3]. The project evaluates the efficacy of Transformer-based semantic analysis against traditional keyword-based and shallow machine learning techniques[cite: 3].

## Authors
* **Chaulagai Shishir** (20240301022)[cite: 1]
* **Bishwokarma Rajkumar** (20240301097)[cite: 1]
* **Mehta Avishek** (20240301059)[cite: 1]

**Institution:** College of Global AI Convergence, Seoul Christian University, Korea[cite: 1]

---

## Project Overview

Mobile SMS spam poses a significant cybersecurity threat, with traditional rule-based and shallow machine learning systems struggling against obfuscation and semantic manipulation[cite: 3]. This project provides an empirical comparison of three distinct classification paradigms to determine the most effective approach for identifying malicious messages[cite: 3, 15]. 

The primary metric of success in this security context is **Recall** (minimizing missed spam/false negatives) while maintaining a low false positive rate[cite: 16].

### Models Implemented
1. **TF-IDF with Logistic Regression (Baseline):** Represents traditional keyword-based filtering using a sparse bag-of-words approach and a 3,000-term vocabulary[cite: 15, 18].
2. **Embedding and Bidirectional LSTM (BiLSTM):** Represents sequential deep learning, utilizing learned dense word embeddings and capturing bidirectional context[cite: 15, 18].
3. **Fine-Tuned DistilBERT (Proposed Model):** A Transformer-based approach utilizing contextual subword embeddings (66 million parameters) to capture full semantic context and long-range dependencies[cite: 15, 19].

---

## Dataset

The study utilizes the **UCI SMS Spam Collection**, a benchmark dataset containing 5,572 labeled English SMS messages[cite: 8].

* **Class Distribution:** 4,825 legitimate (ham) messages (86.6%) and 747 spam messages (13.4%)[cite: 8, 10].
* **Data Splits:** Stratified sampling was used to partition the data into 70% Training (3,900 messages), 15% Validation (836 messages), and 15% Testing (836 messages)[cite: 14].

---

## Performance and Results

All models were evaluated on the identical held-out test set of 836 messages[cite: 22]. The fine-tuned DistilBERT model significantly outperformed the baselines, particularly in reducing false negatives[cite: 23, 24].

| Model | Accuracy | Precision | Recall | F1-score | ROC-AUC |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **TF-IDF + Logistic Regression** | 0.9737[cite: 23] | 0.9592[cite: 23] | 0.8393[cite: 23] | 0.8952[cite: 23] | 0.9896[cite: 23] |
| **Embedding + BiLSTM** | 0.9773[cite: 23] | 0.9697[cite: 23] | 0.8571[cite: 23] | 0.9100[cite: 23] | 0.9858[cite: 23] |
| **DistilBERT (Transformer)** | **0.9928**[cite: 23] | **0.9732**[cite: 23] | **0.9732**[cite: 23] | **0.9732**[cite: 23] | **0.9990**[cite: 23] |

**Key Findings:**
* DistilBERT reduced the number of missed spam messages (false negatives) from 18 (Baseline) to 3, representing an 83.3% reduction[cite: 24].
* Qualitative semantic context evaluation demonstrated that the Transformer successfully identified obfuscated phishing attempts, social engineering with conversational disguises, and explicit spam that the TF-IDF model missed[cite: 25].
* The Transformer also successfully avoided false alarms on legitimate messages containing unusual vocabulary (e.g., "tsunamis", "volcanoes") by understanding the non-commercial context[cite: 26].

---

## Experimental Setup

The experiments were conducted in the following environment[cite: 21]:
* **Hardware:** NVIDIA Tesla T4 GPU (16 GB VRAM), 2-core Intel Xeon CPU, 12 GB RAM[cite: 21].
* **Software/Libraries:**
  * Ubuntu 20.04 LTS[cite: 21]
  * Python 3.8.10[cite: 21]
  * PyTorch 2.0.1[cite: 21]
  * Hugging Face Transformers 4.30.2[cite: 21]
  * scikit-learn 1.2.2[cite: 21]
  * NumPy 1.23.5[cite: 21]
  * Pandas 1.5.3[cite: 21]

### Installation

```bash
# Clone the repository
git clone [https://github.com/yourusername/sms-spam-detection.git](https://github.com/yourusername/sms-spam-detection.git)
cd sms-spam-detection

# Install dependencies
pip install -r requirements.txt
