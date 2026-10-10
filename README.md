# A Transformer-Based Classification: A Case Study of Semantic Context Evaluation for Mobile Spam Message Detection

This repository contains the implementation, evaluation, and documentation for a comparative study on mobile SMS spam and phishing (smishing) detection. The project evaluates the efficacy of Transformer-based semantic analysis against traditional keyword-based and shallow machine learning techniques.

## Authors

* **Chaulagai Shishir** (20240301022)


* **Bishwokarma Rajkumar** (20240301097)


* **Mehta Avishek** (20240301059)



**Institution:** College of Global AI Convergence, Seoul Christian University, Korea

---

## Project Overview

Mobile SMS spam poses a significant cybersecurity threat, with traditional rule-based and shallow machine learning systems struggling against obfuscation and semantic manipulation. This project provides an empirical comparison of three distinct classification paradigms to determine the most effective approach for identifying malicious messages.

The primary metric of success in this security context is **Recall** (minimizing missed spam/false negatives) while maintaining a low false positive rate.

### Models Implemented

1. **TF-IDF with Logistic Regression (Baseline):** Represents traditional keyword-based filtering using a sparse bag-of-words approach and a 3,000-term vocabulary.


2. **Embedding and Bidirectional LSTM (BiLSTM):** Represents sequential deep learning, utilizing learned dense word embeddings and capturing bidirectional context.


3. **Fine-Tuned DistilBERT (Proposed Model):** A Transformer-based approach utilizing contextual subword embeddings (66 million parameters) to capture full semantic context and long-range dependencies.



---

## Dataset

The study utilizes the **UCI SMS Spam Collection**, a benchmark dataset containing 5,572 labeled English SMS messages.

* **Class Distribution:** 4,825 legitimate (ham) messages (86.6%) and 747 spam messages (13.4%).


* **Data Splits:** Stratified sampling was used to partition the data into 70% Training (3,900 messages), 15% Validation (836 messages), and 15% Testing (836 messages).



---

## Performance and Results

All models were evaluated on the identical held-out test set of 836 messages. The fine-tuned DistilBERT model significantly outperformed the baselines, particularly in reducing false negatives.

| Model | Accuracy | Precision | Recall | F1-score | ROC-AUC |
| --- | --- | --- | --- | --- | --- |
| **TF-IDF + Logistic Regression** | 0.9737

 | 0.9592

 | 0.8393

 | 0.8952

 | 0.9896

 |
| **Embedding + BiLSTM** | 0.9773

 | 0.9697

 | 0.8571

 | 0.9100

 | 0.9858

 |
| **DistilBERT (Transformer)** | **0.9928**<br> | **0.9732**<br> | **0.9732**<br> | **0.9732**<br> | **0.9990**<br> |

**Key Findings:**

* DistilBERT reduced the number of missed spam messages (false negatives) from 18 (Baseline) to 3, representing an 83.3% reduction.


* Qualitative semantic context evaluation demonstrated that the Transformer successfully identified obfuscated phishing attempts, social engineering with conversational disguises, and explicit spam that the TF-IDF model missed.


* The Transformer also successfully avoided false alarms on legitimate messages containing unusual vocabulary (e.g., "tsunamis", "volcanoes") by understanding the non-commercial context.



---

## Experimental Setup

The experiments were conducted in the following environment:

* **Hardware:** NVIDIA Tesla T4 GPU (16 GB VRAM), 2-core Intel Xeon CPU, 12 GB RAM.


* **Software/Libraries:**
* Ubuntu 20.04 LTS


* Python 3.8.10


* PyTorch 2.0.1


* Hugging Face Transformers 4.30.2


* scikit-learn 1.2.2


* NumPy 1.23.5


* Pandas 1.5.3





### Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/sms-spam-detection.git
cd sms-spam-detection

# Install dependencies
pip install -r requirements.txt

```
