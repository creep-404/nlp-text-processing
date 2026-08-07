# 📝 NLP Text Processing

A Python project demonstrating fundamental **Natural Language Processing (NLP)** preprocessing techniques using an **Emotions Dataset**. This project covers text cleaning, label encoding, stopword removal, and dataset preparation for machine learning applications.

---

## 📌 Project Objectives

This project performs the following NLP preprocessing tasks:

- Load the Emotions Dataset
- Encode categorical emotion labels
- Convert text to lowercase
- Remove punctuation
- Remove numbers
- Remove emojis and non-ASCII characters
- Remove English stopwords
- Combine all preprocessing steps into a single cleaning pipeline
- Calculate text lengths
- Visualize text length distribution
- Save the cleaned dataset
- Analyze emotion distribution

---

## 📂 Dataset

Dataset used:

- **train.txt**
- Format:
  ```
  text;emotion
  ```

Example:

```
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
- Regular Expressions (re)

---

## 📚 Tasks Completed

### ✅ Question 1
- Loaded the Emotions Dataset
- Displayed the first 10 rows
- Displayed dataset shape
- Checked for missing values

---

### ✅ Question 2
- Encoded emotion labels using LabelEncoder
- Displayed unique emotion labels
- Created emotion-to-numeric mapping

---

### ✅ Question 3
- Converted all text to lowercase
- Compared text before and after lowercasing

---

### ✅ Question 4
- Removed punctuation marks
- Displayed cleaned text samples

---

### ✅ Question 5
- Removed numerical digits
- Displayed text before and after cleaning

---

### ✅ Question 6
- Removed emojis and special Unicode symbols
- Kept only ASCII characters

---

### ✅ Question 7
- Downloaded NLTK stopwords
- Removed English stopwords
- Displayed cleaned text samples

---

### ✅ Question 8
- Combined all preprocessing steps into one function
- Created a new column:
  ```
  cleaned_text
  ```
- Compared original and cleaned text

---

### ✅ Question 9
- Calculated text length
- Plotted histogram of cleaned text lengths
- Computed:
  - Average text length
  - Minimum text length
  - Maximum text length

---

### ✅ Question 10
- Applied the complete preprocessing pipeline
- Saved cleaned dataset as:

```
cleaned_emotions.csv
```

- Displayed emotion frequency distribution

---

## 📊 Output

Generated files:

```
cleaned_emotions.csv
```

The dataset contains:

- Original text
- Emotion label
- Encoded emotion
- Cleaned text

---

## 📈 Example Cleaning Pipeline

Original Text

```
I AM Feeling Happy!!! 😊😊 2024
```

↓

Lowercase

```
i am feeling happy!!! 😊😊 2024
```

↓

Remove Punctuation

```
i am feeling happy 😊😊 2024
```

↓

Remove Numbers

```
i am feeling happy 😊😊
```

↓

Remove Emojis

```
i am feeling happy
```

↓

Remove Stopwords

```
feeling happy
```

---

## 📦 Installation

Clone the repository

```bash
git clone https://github.com/creep-404/nlp-text-processing.git
```

Install dependencies

```bash
pip install pandas nltk scikit-learn matplotlib
```

---

## ▶️ Run

```bash
python preprocessing.py
```

or open the Jupyter Notebook:

```
nlp-text-processing.ipynb
```

---

## 👨‍💻 Author

**Ahmad**

GitHub: https://github.com/creep-404