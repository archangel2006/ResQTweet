# 🌪️ ResQTweet
**AI-powered Real-Time Disaster Tweet Classification & Alerting System**  

![ResQTweet Banner](https://img.shields.io/badge/ResQTweet-Crisis%20Detection-blue)   ![Natural Language Processing with Disaster Tweets](https://img.shields.io/badge/Natural%20Language%20Processing%20with%20Disaster%20Tweets-black)   

![Hackathon](https://img.shields.io/badge/Global%20AI-Buildathon%202025-purple)  [![YouTube Pitch](https://img.shields.io/badge/YouTube-Pitch-red?logo=youtube)](https://www.youtube.com/watch?v=https://youtu.be/FGQlL3H_-oA?si=oMMIbS4riez-0IOU)


![SDG 11](https://img.shields.io/badge/SDG-11%20Sustainable%20Cities%20&%20Communities-yellow)   ![SDG 13](https://img.shields.io/badge/SDG-13%20Climate%20Action-brightgreen)  

![Built using Colab](https://img.shields.io/badge/Built%20using-Colab-orange) ![Python](https://img.shields.io/badge/Python-3.13-blue) ![Scikit-learn](https://img.shields.io/badge/scikit--learn-ML-orange) ![HuggingFace](https://img.shields.io/badge/HuggingFace-NLP-lightgrey)

---

## 🌍 Sustainable Development Goals (SDGs)
- 🌆 **SDG 11 – Sustainable Cities and Communities**: Safer, more resilient cities with disaster-preparedness tools.  
- 🌍 **SDG 13 – Climate Action**: Timely action against climate-related disasters through early detection.  

---

# 🎯 Problem
During natural disasters or humanitarian crises, timely information is critical.  
- Twitter (X) provides real-time updates but is often noisy or metaphorical.  
- Distinguishing real disaster tweets from irrelevant chatter is difficult.  
**Challenge:** Automatically detect genuine disaster-related tweets to assist responders, NGOs, and media in rapid situational awareness.


---

# ✅ Solution

**ResQTweet** leverages NLP + ML + summarization to:
- Preprocess and clean tweets.  
- Extract TF-IDF features from text and keywords.  
- Classify tweets as **disaster** or **non-disaster** using ML models.  
- Summarize disaster tweets with HuggingFace DistilBART for concise alerts. 

---
# ✨ Key Features

- **Real-time Detection**: Classifies tweets instantly with a lightweight ML model.  
- **Alert Generation**: Produces human-readable, concise alerts.  
- **Keyword + Semantic Understanding**: Captures context beyond simple keyword matches.  
- **Scalable & Extensible**: Future multilingual support for global crises.  
---

# ⚙️ Tech Stack
| Layer              | Tools & Frameworks |
|--------------------|---------------------|
| **Programming**    | Python |
| **Data Handling**  | Pandas, NumPy |
| **ML Models**      | Scikit-learn (Logistic Regression, Naïve Bayes) |
| **NLP**            | Hugging Face Transformers (DistilBART) |
| **Vectorization**  | TF-IDF (unigrams + bigrams) |
| **Visualization**  | Matplotlib, Seaborn |
| **Deployment (Future)** | Streamlit / Dash + Twitter API |
| **Environment**    | Google Colab |

- **Dataset**: [Natural Language Processing with Disaster Tweets](https://www.kaggle.com/competitions/nlp-getting-started/data)
---

# 📊 Model Details & Performance

**Algorithms Evaluated**: Multinomial Naïve Bayes, Complement Naïve Bayes, Logistic Regression

**Features**: TF-IDF vectors (text + keyword) + binary keyword flag



| Model                   | Accuracy   | Precision | Recall | F1-score |
| ----------------------- | ---------- | --------- | ------ | -------- |
| MultinomialNB           | 81.29%     | 0.816     | 0.728  | 0.770    |
| ComplementNB            | 80.70%     | 0.785     | 0.758  | 0.771    |
| **Logistic Regression** | **81.48%** | 0.804     | 0.752  | 0.777    |


📌 **Best model** → Logistic Regression (balanced accuracy & F1).  

---

# 🔄 Process Pipeline
```
              ┌─────────────────────────────┐
              │   Load tweets_data.csv      │
              │                             │
              └─────────────┬───────────────┘
                            │
                 ┌──────────▼─────────────┐
                 │     Preprocessing      │
                 │    - Clean text &      |
                 |       keyword columns  │
                 │    - Remove URLs,      |
                 |      mentions,hashtags,|
                 |   non-alphabetic chars │
                 │  - Lowercase all text  │
                 │  - Remove extra spaces │
                 │  - Handle NaNs         │
                 │  - Drop irrelevant cols│
                 └──────────┬─────────────┘
                            │
          ┌─────────────────┴─────────────────┐
          │                                   │
 ┌────────▼─────────┐                 ┌────────▼─────────┐
 │  TF-IDF on text  │                 │ TF-IDF on keyword│
 │  (unigrams+bigrams, top 6000) │    │  (unigrams, all) │
 └────────┬─────────┘                 └────────┬─────────┘
          │                                   │
          └─────────────┬─────────────────────┘
                        ▼
      ┌───────────────────────────────────────────────┐
      │          Combine Features (hstack)            │
      │ [text TF-IDF + keyword TF-IDF + keyword_flag] │
      └───────────────────────────┬───────────────────┘
                         │
             ┌───────────▼───────────────┐
             │   Split train/validation  │
             │   (stratified 80-20 split)│
             └───────────┬───────────────┘
                         │
             ┌───────────▼───────────────┐
             │        Train Model        │
             │     LogisticRegression    │
             │       MultinomialNB       |
             |       ComplementNB        │
             └───────────┬───────────────┘
                         │
             ┌───────────▼───────────────┐
             │   Evaluate Model          │
             │ Accuracy / F1-score /     │
             │ Confusion Matrix          │
             └───────────┬───────────────┘
                         │
             ┌───────────▼───────────────┐
             │   Save / Select Best Model│
             │ LogisticRegression chosen │
             └───────────┬───────────────┘
                         │
             ┌───────────▼───────────────┐
             │   Predict on New Tweets   │
             │   (raw text input)        │
             └───────────┬───────────────┘
                         │
             ┌───────────▼───────────────┐
             │  Generate Alerts          │
             │  - Summarize if disaster  │
             │  - Return 🚨 or ✅       │
             └───────────────────────────┘

```
---

## 🚨 Sample Outputs
```
disaster_alert_system("Earthquake of 6.1 magnitude hits California.")
# 🚨 DISASTER ALERT: Earthquake of 6.1 magnitude hits California.

disaster_alert_system("Huge flood of messages in my inbox 😂")
# ✅ No disaster detected.

disaster_alert_system("Explosion at chemical plant in Houston, authorities evacuating nearby areas.")
# 🚨 DISASTER ALERT: Explosion at chemical plant in Houston, authorities evacuating nearby areas.
```
---
# 📂 Project Structure

```
ResQTweet/
│── Code/                  # Code (.ipynb) & Dataset (tweets_data.csv)
│   ├── ResQTweet.ipynb
│   ├── tweets_data.csv
│── WriteUp/                   # Core scripts
│   ├── WriteUp.md
│   ├── Word Documet
│
│── requirements.txt       # Dependencies
│── README.md              # Project documentation
```

---
# 🌟 Impact

🏛️ Governments: Faster disaster response & prioritization

🆘 NGOs: Smarter humanitarian aid allocation

📰 Media: Early verification of breaking crises

🌎 Future: Multilingual expansion for global early-warning system

---
# 👩‍💻 Author

Vaibhavi Srivastava

🔗 Github : [archangel2006](https://github.com/archangel2006)

📅 Hackathon : Global AI Buildathon 2025
