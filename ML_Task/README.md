# ML Task: Financial Sentiment Analysis

This project contains 3 levels of sentiment classification on the `takala/financial_phrasebank` dataset using different approaches.

## Folder Contents

- `ML_Task_Level_1.ipynb` → TF-IDF + Logistic Regression
- `ML_Task_Level_2.ipynb` → Transformer Zero-Shot Classification
- `ML_Task_Level_3.ipynb` → DistilBERT Fine-Tuning with LoRA
- `README.md` → Steps to reproduce the results

---

## Dataset

Dataset used: `takala/financial_phrasebank`  
Split used: `sentences_allagree`

This dataset contains financial sentences with sentiment labels:
- 0 = negative
- 1 = neutral
- 2 = positive

---

## Level 1: TF-IDF + Logistic Regression

### Approach
In Level 1, a traditional machine learning approach is used.
The text is converted into numerical features using TF-IDF, and then a Logistic Regression classifier is trained.

### Main Steps
1. Load dataset
2. Convert dataset to pandas DataFrame
3. Check class counts and balance
4. Split into training and testing sets (80-20)
5. Apply TF-IDF vectorization
6. Train Logistic Regression model
7. Evaluate using Precision, Recall, F1-score
8. Plot confusion matrix

---

## Level 2: Transformer Zero-Shot Classification

### Approach
In Level 2, a pretrained transformer model is used in zero-shot mode.
No training is done. The model directly predicts among the labels:
- negative
- neutral
- positive

### Main Steps
1. Load dataset / use test split
2. Load transformer pipeline for zero-shot classification
3. Pass test sentences one by one
4. Get predicted labels
5. Convert string labels to numeric format
6. Evaluate using Precision, Recall, F1-score
7. Plot confusion matrix

---

## Level 3: DistilBERT Fine-Tuning with LoRA

### Approach
In Level 3, `distilbert-base-uncased` is fine-tuned on the dataset using LoRA.
LoRA is used to reduce the number of trainable parameters and make fine-tuning efficient.

### Main Steps
1. Load dataset
2. Create train-test split
3. Load tokenizer
4. Tokenize dataset using `map()`
5. Load `AutoModelForSequenceClassification` with `num_labels=3`
6. Apply LoRA using `LoraConfig`
7. Print trainable parameters
8. Define `TrainingArguments`
9. Train model using `Trainer`
10. Predict on test set
11. Evaluate using Precision, Recall, F1-score
12. Plot confusion matrix
13. Compare Level 1, Level 2, and Level 3

---

## Installation

Run the following before using the notebooks:

```python
!pip install transformers datasets peft accelerate scikit-learn matplotlib seaborn pandas
