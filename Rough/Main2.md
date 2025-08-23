# 🌍 Disaster Alert Tweet Classifier

An AI-powered solution to detect **disaster-related tweets in real time**, enabling faster crisis response and supporting **Sustainable Development Goal 11 (Sustainable Cities and Communities)**.

## 🚀 Problem
During disasters (earthquakes, floods, wildfires, conflicts), people post on Twitter/X instantly. However, identifying which tweets are truly related to disasters is difficult due to noise and irrelevant chatter. Emergency response teams lose valuable time in manual filtering.

## 💡 Solution
We built a machine learning model that classifies tweets into:
- **Disaster-related**
- **Not disaster-related**

This system can help governments, NGOs, and first responders identify urgent situations and allocate resources efficiently.

## ⚙️ Tech Stack
- **Python** 🐍
- **NLP**: Text cleaning, TF-IDF embeddings
- **Models**: Logistic Regression / Hugging Face DistilBERT
- **Libraries**: `scikit-learn`, `transformers`, `pandas`, `numpy`
- **Visualization**: Matplotlib / Seaborn
- (Optional) **HuggingFace Spaces** for deployment

## 🛠️ Dataset
- Source: [Kaggle Disaster Tweets Dataset](https://www.kaggle.com/competitions/nlp-getting-started)
- 10,000+ tweets with binary labels (`1 = disaster`, `0 = not disaster`)
- Columns: `id`, `keyword`, `text`, `target`

## 🔍 Methodology
1. **Data Cleaning**:  
   - Removed missing values, cleaned text (lowercasing, stopword removal, stemming).
   - Removed noisy columns like `location`.

2. **Feature Engineering**:  
   - **Text** → TF-IDF (word + bi-gram features).  
   - **Keyword** → TF-IDF separately.  
   - Combined features into a sparse matrix.

3. **Model Training**:  
   - Baseline: Logistic Regression & Random Forest.  
   - Advanced: HuggingFace DistilBERT fine-tuned on the dataset.

4. **Evaluation**:  
   - Metrics: Accuracy, Precision, Recall, F1-score.  
   - Achieved F1 ≈ **0.82** with Logistic Regression.  
   - DistilBERT (small model) improved results further.

## 🌍 Impact
- Helps **disaster management agencies** monitor social media in real-time.
- Scalable to **other languages and platforms** (Reddit, news articles).
- Aligns with **SDG 11: Sustainable Cities and Communities**.

## 📈 Future Work
- Real-time integration with **Twitter API**.
- Geo-location mapping for disaster intensity.
- Dashboard for first responders.

## 📹 Demo
👉 [Add YouTube link here after recording the 3-minute demo]

---

## 👩‍💻 Contributors
Built with ❤️ for the **Global AI Buildathon 2025**.
