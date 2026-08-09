# 📝 NLP Text Processing & Emotion Classification

A Python project demonstrating fundamental **Natural Language Processing (NLP)** preprocessing and text classification techniques using an **Emotions Dataset**.

The project covers text cleaning, label encoding, Bag of Words, TF-IDF, n-grams, Multinomial Naive Bayes classification, model comparison, and saving the best trained model for future predictions.

---

## 📌 Project Objectives

This project covers the complete NLP workflow:

- Load the Emotions Dataset
- Encode categorical emotion labels
- Clean and preprocess text
- Convert text into numerical features
- Apply Bag of Words
- Apply unigram and bigram features
- Apply TF-IDF
- Train Multinomial Naive Bayes models
- Compare model accuracy
- Analyze text length distribution
- Save the cleaned dataset
- Save the best vectorizer and trained model
- Use the saved model for future emotion predictions

---

## 📂 Dataset

Dataset used:

- **train.txt**

Format:

```text
text;emotion
```

Example:

```text
i didnt feel humiliated;sadness
i can go from feeling so hopeless to hopeful;joy
```

---

## 🛠 Technologies Used

- Python 3.10
- Pandas
- NLTK
- Scikit-learn
- Matplotlib
- Joblib
- Regular Expressions (`re`)

---

# 📚 NLP Preprocessing

## ✅ Question 1 — Load and Explore Dataset

- Loaded the Emotions Dataset
- Displayed the first rows
- Checked dataset shape
- Inspected the dataset structure

---

## ✅ Question 2 — Encode Emotion Labels

Used `LabelEncoder` to convert emotion labels into numerical values.

Example:

```text
sadness → numerical code
joy     → numerical code
anger   → numerical code
```

The emotion-to-number mapping was also displayed.

---

## ✅ Question 3 — Lowercasing

Converted the entire text column to lowercase.

Example:

```text
I AM Feeling Happy
```

becomes:

```text
i am feeling happy
```

This helps make text representations more consistent.

---

## ✅ Question 4 — Remove Punctuation

Removed punctuation marks from the text.

Example:

```text
I am happy!!!
```

becomes:

```text
I am happy
```

---

## ✅ Question 5 — Remove Digits

Removed numerical digits from the text.

Example:

```text
I am happy 2024
```

becomes:

```text
I am happy
```

---

## ✅ Question 6 — Remove Emojis and Special Symbols

Kept only ASCII characters to remove emojis and other non-ASCII symbols.

Example:

```text
I am happy 😊
```

becomes:

```text
I am happy
```

---

## ✅ Question 7 — Remove Stopwords

Used NLTK English stopwords to remove common words that provide limited information for basic NLP classification.

Example:

```text
I am feeling very happy
```

can become:

```text
feeling happy
```

---

## ✅ Question 8 — Complete Text Cleaning Pipeline

Combined all preprocessing steps into a single cleaning function:

```text
Original Text
      ↓
Lowercase
      ↓
Remove Punctuation
      ↓
Remove Numbers
      ↓
Remove Emojis / Non-ASCII Characters
      ↓
Remove Stopwords
      ↓
Cleaned Text
```

Created a new column:

```text
cleaned_text
```

The original and cleaned text were compared side by side.

---

## ✅ Question 9 — Text Length Analysis

Calculated the number of words in each cleaned text.

Also calculated:

- Average text length
- Minimum text length
- Maximum text length

A histogram was created to visualize the distribution of cleaned text lengths.

---

## ✅ Question 10 — Save Cleaned Dataset

Applied the complete cleaning pipeline and saved the resulting dataset as:

```text
cleaned_emotions.csv
```

The cleaned dataset contains:

- Original text
- Emotion label
- Encoded emotion
- Cleaned text

---

# 🤖 Machine Learning

## ✅ Question 11 — Train-Test Split

Separated the dataset into:

```text
X → cleaned text
y → emotion labels
```

Used:

```python
test_size=0.20
random_state=42
```

This creates an **80% training set** and **20% testing set**.

---

# 🔢 Feature Extraction

## ✅ Question 12 — Bag of Words

Applied `CountVectorizer` to convert text into numerical Bag-of-Words features.

The vectorizer was:

- Fit on `X_train`
- Used to transform `X_test`

The training and testing feature matrix shapes were displayed.

The first 20 vocabulary features were also displayed.

---

## ✅ Question 13 — Multinomial Naive Bayes with Bag of Words

Trained a `MultinomialNB` model using the Bag-of-Words features.

Steps:

```text
X_train
   ↓
CountVectorizer
   ↓
Bag-of-Words Features
   ↓
MultinomialNB
   ↓
Predictions
   ↓
Accuracy
```

The accuracy on the test set was calculated.

---

## ✅ Question 14 — Vocabulary Analysis

Using the fitted `CountVectorizer`:

- Printed the total vocabulary size
- Displayed 15 vocabulary words
- Converted one training document into a Bag-of-Words vector

The resulting vector represents the frequency of vocabulary words within the selected document.

---

## ✅ Question 15 — Unigrams + Bigrams

Created a new `CountVectorizer` using:

```python
ngram_range=(1, 2)
```

This generates:

### Unigrams

```text
happy
feeling
today
```

### Bigrams

```text
feeling happy
happy today
```

Both unigrams and bigrams were used as features.

---

## ✅ Question 16 — Bigram Multinomial Naive Bayes

Trained another `MultinomialNB` model using the unigram + bigram features.

The accuracy was compared with the basic unigram Bag-of-Words model.

---

# 📊 TF-IDF

## ✅ Question 17 — TF-IDF Vectorization

Applied `TfidfVectorizer` to the same train-test split.

Steps:

```text
X_train → fit_transform()
X_test  → transform()
```

The TF-IDF matrix shapes and first 15 feature names were displayed.

---

## ✅ Question 18 — Multinomial Naive Bayes with TF-IDF

Trained a `MultinomialNB` classifier using TF-IDF features.

The model was evaluated using the test set and its accuracy was calculated.

---

# 📈 Model Comparison

Three approaches were compared using the same train-test split:

| Approach | Features |
|---|---|
| Bag of Words | Unigrams |
| Bag of Words | Unigrams + Bigrams |
| TF-IDF | TF-IDF weighted features |

Each approach was trained using:

```text
Multinomial Naive Bayes
```

Their test accuracies were compared to determine which representation performed best.

### Observation

The best method depends on the actual accuracy obtained from the dataset.

In general:

- **Unigrams** capture individual word information.
- **Bigrams** provide additional short-range context through word combinations.
- **TF-IDF** gives higher importance to informative words while reducing the influence of very common words.

---

# 🏆 Best Model Selection

The final pipeline automatically compares:

```text
CountVectorizer + MultinomialNB
              VS
TF-IDF + MultinomialNB
```

The approach with the highest test accuracy is selected as the best model.

The corresponding vectorizer and trained model are then saved using `joblib`.

---

# 💾 Saved Model Files

After running the final model-selection code, the following files are created:

```text
best_vectorizer.pkl
best_emotion_model.pkl
```

### `best_vectorizer.pkl`

Contains the fitted vectorizer used by the best-performing model.

It can be either:

```text
CountVectorizer
```

or:

```text
TfidfVectorizer
```

### `best_emotion_model.pkl`

Contains the trained:

```text
MultinomialNB
```

model.

---

# 🔮 Using the Saved Model

The saved model can be loaded without retraining:

```python
import joblib

# Load the saved vectorizer and model
vectorizer = joblib.load("best_vectorizer.pkl")
model = joblib.load("best_emotion_model.pkl")

# New text
text = ["i am feeling very happy today"]

# Convert text into features
text_vector = vectorizer.transform(text)

# Predict emotion
prediction = model.predict(text_vector)

print("Predicted emotion:", prediction[0])
```

This allows the trained model to classify new text using the same feature extraction process used during training.

---

# 📁 Project Structure

```text
nlp-text-processing/
│
├── train.txt
├── cleaned_emotions.csv
│
├── best_vectorizer.pkl
├── best_emotion_model.pkl
│
├── preprocessing.py
├── nlp-text-processing.ipynb
│
├── README.md
└── requirements.txt
```

---

# 📦 Installation

Clone the repository:

```bash
git clone https://github.com/creep-404/nlp-text-processing.git
```

Move into the project directory:

```bash
cd nlp-text-processing
```

Install the required libraries:

```bash
pip install pandas nltk scikit-learn matplotlib joblib
```

---

# ▶️ Run the Project

Run the Python script:

```bash
python preprocessing.py
```

Or open the Jupyter Notebook:

```text
nlp-text-processing.ipynb
```

---

# 🔄 Complete NLP Workflow

The complete project workflow is:

```text
                Emotions Dataset
                       │
                       ▼
                  Load Dataset
                       │
                       ▼
                 Text Cleaning
                       │
        ┌──────────────┼──────────────┐
        │              │              │
    Lowercase      Punctuation      Numbers
        │              │              │
        └──────────────┼──────────────┘
                       ▼
              Emojis / Symbols
                       │
                       ▼
                 Stopword Removal
                       │
                       ▼
                cleaned_text
                       │
                       ▼
                Train-Test Split
                       │
             ┌─────────┴─────────┐
             │                   │
             ▼                   ▼
      CountVectorizer       TfidfVectorizer
             │                   │
             ▼                   ▼
      MultinomialNB        MultinomialNB
             │                   │
             └─────────┬─────────┘
                       ▼
                Accuracy Comparison
                       │
                       ▼
                 Best Model
                       │
                       ▼
              Save with Joblib
                       │
              ┌────────┴────────┐
              ▼                 ▼
       best_vectorizer.pkl   best_emotion_model.pkl
```

---

# 📊 Key Concepts Demonstrated

This project demonstrates practical implementation of:

- Text preprocessing
- NLP data cleaning
- Stopword removal
- Label encoding
- Train-test splitting
- Bag-of-Words
- N-grams
- Unigrams
- Bigrams
- TF-IDF
- Multinomial Naive Bayes
- Model evaluation
- Accuracy comparison
- Model serialization with Joblib
- Text emotion classification

---

## 👨‍💻 Author

**Ahmad**

GitHub:

```text
https://github.com/creep-404
```

---

## 📌 Project Status

**Completed**

The project covers the complete workflow from raw text preprocessing to feature extraction, machine learning classification, model comparison, and saving the best-performing model for future use.