# 🌪️ DisasterAlert: Real-Time Tweet Classification for Crisis Detection

A lightweight NLP-powered project to identify real-time disaster-related tweets using machine learning, and provide concise summaries for rapid response.

## 🚀 Overview

In times of crisis, social media becomes a vital source of real-time information. This project aims to detect whether a tweet refers to an actual disaster or not, using NLP techniques, and if so, generate a short summary for alerting purposes. Built for the Global AI Buildathon Hackathon 2025.

## 📂 Dataset

Used the [Real or Not? NLP with Disaster Tweets](https://www.kaggle.com/competitions/nlp-getting-started/data) dataset from Kaggle, which includes:
- `text`: raw tweet content
- `keyword`: disaster-related term (optional)
- `target`: 1 if disaster, 0 if not

## 🛠️ Tech Stack

- Python
- scikit-learn (Logistic Regression)
- HuggingFace Transformers (BART for summarization)
- TfidfVectorizer for feature extraction
- Jupyter Notebook / HuggingFace Spaces

## 📊 Pipeline Summary

1. **Data Cleaning**:
   - Remove URLs, mentions, hashtags, punctuations
   - Lowercasing, stripping extra spaces

2. **Feature Engineering**:
   - Use TF-IDF Vectorizer on both `text` and `keyword` columns
   - Combine the features using `hstack` (sparse matrix)

3. **Modeling**:
   - Logistic Regression for binary classification
   - Evaluated using accuracy, precision, recall, F1-score

4. **Summarization**:
   - BART (via HuggingFace pipeline) to generate brief alerts for detected disaster tweets

5. **Alert System**:
   - Wrap everything in a single function: takes a tweet and returns either ✅ or 🚨 with a summary

## 🔍 Example Output

```python
disaster_alert_system("Earthquake of 6.1 magnitude hits California.")
# 🚨 ALERT: Earthquake hits California

disaster_alert_system("Happy birthday to my dog 🎂🐶")
# ✅ No disaster detected.
```



# 🧠 Why This Matters

This tool can be integrated into:

Disaster monitoring dashboards

Social media scrapers

Emergency alert bots

Real-time crisis response tools

---
# ♻️ Future Work

Live integration with Twitter API

Dashboard for alert visualization

Multilingual disaster detection

Named Entity Recognition for extracting locations

🧑‍💻 Author

Made with ♥️ during the [Global AI Buildathon Hackathon 2025] by [Your Name].
