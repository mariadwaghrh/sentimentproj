# Aspect-Based Sentiment Analysis (ABSA) for Big Data

**Course:** Sentiment Analysis of Big Data  
**By:** Maria Dwaghrh, Hala Alzoubi, Quds Albreim  
**Date:** May 2026

---

## What is this project?

Standard sentiment analysis gives one label (Positive/Negative) to an entire sentence. This is too simple for real feedback. For example: *"I love the university, but the exams are stressful"* — two different sentiments in one sentence.

This project builds an **Aspect-Based Sentiment Analysis (ABSA)** pipeline that:
1. **Identifies the topic** (Education, Career, Relationships, Mental Health, Health & Body)
2. **Classifies the sentiment** toward that specific topic (Positive, Negative, Neutral)

---

## Dataset

- **Source:** [Emotions Dataset on Kaggle](https://kaggle.com/datasets/nelgiriyewithana/emotions)
- **Size:** 416,809 records
- **Original labels:** Sadness, Joy, Love, Anger, Fear, Surprise
- **Mapped to:** Positive (Joy + Love), Negative (Sadness + Anger + Fear), Neutral (Surprise)

> ⚠️ Download the dataset from Kaggle and place `emotions.csv` in the project folder before running.

---

## Project Pipeline

```
Raw Text → Aspect Identification → Text Cleaning → Tokenization → LSTM Model → Sentiment
```

### 1. Aspect Identification
Fast keyword-based function using Python set intersection (O(1) speed) to detect:
-  Education
-  Work & Career
-  Relationships
-  Mental Health
- Health & Body
- General (fallback)

### 2. Text Preprocessing
- Lowercase normalization + punctuation removal
- Tokenization with 5,000-word vocabulary
- Sequence padding to fixed length of 40 words

### 3. LSTM Model (TensorFlow/Keras)
```
Embedding(5000, 32)
→ Dropout(0.5)
→ LSTM(16, L2 regularization)
→ Dropout(0.5)
→ Dense(32, relu)
→ Dense(3, softmax)
```

### 4. Handling Class Imbalance
Neutral class was only 3.6% of data. Used `class_weight` to penalize misclassification of minority class — fixing the "Accuracy Paradox."

---

## Results

| Metric | Value |
|--------|-------|
| Validation Accuracy | ~97.2% |
| Neutral samples correctly identified | 3,006 |
| Loss (start → end) | 0.39 → 0.13 |

---

## How to Run

1. Clone this repo
2. Download `emotions.csv` from Kaggle (link above) and place it in the folder
3. Install dependencies:
```bash
pip install tensorflow scikit-learn pandas numpy matplotlib seaborn
```
4. Open `ABSA_Proj.ipynb` in Jupyter or Google Colab and run all cells

---

## Files

| File | Description |
|------|-------------|
| `ABSA_Proj.ipynb` | Main notebook with full pipeline |
<<<<<<< HEAD

=======
>>>>>>> a8401cb1ac914f67d947bdc982d8cf755c885369

---

## References

1. Hochreiter, S., & Schmidhuber, J. (1997). Long Short-Term Memory. *Neural Computation*, 9(8), 1735–1780.
2. Chollet, F. (2015). Keras. https://github.com/fchollet/keras
3. Pedregosa, F., et al. (2011). Scikit-learn: Machine Learning in Python. *JMLR*, 12, 2825–2830.
