# 🌪️ ResQTweet 
## Real-Time Crisis Detection from Tweets

- [WordDocument](https://docs.google.com/document/d/1UH-bj_6M9ZDgDoNmzyg2KbySUbh5iX2f0tCdQXBxyhU/edit?usp=sharing)
- Alternate: [DownloadDocument](https://github.com/archangel2006/ResQTweet/blob/main/WriteUp/ResQTweet%20-%20Real-Time%20Crisis%20Detection%20from%20Tweets.docx)

---

# Problem:
In times of natural disasters, conflict, or humanitarian crises, timely information can save lives. Social media, particularly Twitter, has become a critical source of real-time updates. 

However, these updates are often noisy: many tweets use disaster-related keywords metaphorically (“my phone just exploded with notifications”) or in irrelevant contexts. This creates confusion, delays in situational awareness, and difficulty in filtering credible crisis information.

The problem we address is: **How can we automatically distinguish between genuine disaster-related tweets and non-disaster chatter in real-time, to aid faster disaster response and resource allocation?**

---

# Solution:
We propose Disaster Alert Tweet Classifier, an AI-powered pipeline that analyzes tweets and predicts whether they describe a real disaster event.
Our approach combines (NLP) with a binary classification m. The system:
1.	Preprocesses raw tweets by removing noise, URLs, special characters, and stopwords.
2.	Leverages both “keyword” metadata and the full tweet text, ensuring that disaster-indicative terms (e.g., earthquake, flooding, casualties) are captured alongside semantic tweet context.
3.	Uses a trained ML model to classify tweets into two categories: disaster (1) or not disaster (0).


**SDGs Addressed**:

- 🌆 **SDG 11** – Sustainable Cities and Communities: Enhances urban safety & disaster preparedness by monitoring social media for real-time disaster events.
- 🌍 **SDG 13** – Climate Action: Supports early warning systems and rapid response to climate-related disasters.

---

# Tech Stack:
- Python – for data handling and model training
- Pandas, NumPy – preprocessing and dataset management
- Scikit-learn  – baseline ML models (LogisticRegression, NaïveBayes)
- Hugging Face Transformers – advanced NLP (BERT/DistilBERT) for semantic understanding
- TfidfVectorizer  – convert text into numerical features
- Matplotlib/Seaborn – visualizations
- Google Colab – experimentation & reproducibility
- Future Deployments: Twitter API+Streamlit/Dash – for real-time monitoring dashboards

---

# Model Details:
Data Processing & NLP:
 Tweets are cleaned by removing URLs, mentions, hashtags, and non-alphabetic characters, and converted to lowercase. TF-IDF vectorization is applied separately to tweet text and keywords, including unigrams and bigrams. A binary feature indicates the presence of a keyword. This produces high-dimensional sparse vectors representing each tweet.
- Three models were evaluated: Multinomial Naive Bayes, Complement Naive Bayes, and Logistic Regression.
- Features: TF-IDF vectors for text and keywords, plus keyword flag.
- Logistic Regression achieved the best balance of accuracy (81.48%) and F1-score (0.777) for disaster tweets.
- Confusion matrix analysis shows the model effectively distinguishes disaster-related tweets while minimizing false positives.


**Alert Generation**:
 For tweets classified as disasters, a light summarizer (DistilBART) produces concise, human-readable alerts. Short or ultra-short tweets fall back to a trimmed text output.

---

# Impact:
 ResQTweet provides provides a scalable, ethical, and globally inclusive method to detect crises in real time. It can help:
- Disaster management authorities prioritize response efforts.
- Humanitarian organizations allocate resources efficiently.
- Media outlets and NGOs verify early signals of emergencies.
With further development, this system can extend beyond English tweets, making it multilingual and globally impactful.
________________________________________
# Conclusion:
 The project combines NLP, machine learning, and summarization to deliver a practical solution for real-world crisis detection. Its lightweight, scalable architecture ensures usability in live social media streams while keeping computational overhead manageable.

-	VAIBHAVI SRIVASTAVA
-	Github : [archangel2006](https://github.com/archangel2006) 

