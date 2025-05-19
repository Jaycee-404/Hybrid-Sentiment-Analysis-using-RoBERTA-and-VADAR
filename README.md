# Hybrid-Sentiment-Analysis-Combining-RoBERTA-and-VADAR

![MIT License](https://img.shields.io/badge/License-MIT-green.svg)

## Project Overview

Sentiment analysis is key to understanding customer opinions. This project integrates lexicon-based (VADER) and transformer-based (RoBERTa) sentiment scores to leverage their complementary strengths. The hybrid approach improves classification performance by combining traditional and deep learning techniques.

---

## Dataset

This project uses the **Amazon Fine Food Reviews** dataset from Kaggle:

- **Source:** [Amazon Fine Food Reviews - Kaggle](https://www.kaggle.com/datasets/snap/amazon-fine-food-reviews)
- **Context:** Reviews of fine foods on Amazon spanning over 10 years (Oct 1999 - Oct 2012), with ~568,454 reviews.
- **Data Size:**  
  - 568,454 reviews  
  - 256,059 users  
  - 74,258 products  
  - 260 users with more than 50 reviews  

The dataset contains product and user info, ratings, and plain-text reviews, useful for sentiment analysis and recommendation tasks.

---

## Methodology

This project follows a hybrid sentiment analysis approach by combining lexicon-based (VADER) and transformer-based (RoBERTa) sentiment scoring. Below are the detailed steps:

### 1. Data Preprocessing
- Loaded the Amazon Fine Food Reviews dataset.
- Selected relevant columns (`Score`, `Text`) and filtered reviews to form three sentiment classes: Positive (Score ≥ 4), Neutral (Score = 3), and Negative (Score ≤ 2).
- Cleaned the text (lowercasing, removing special characters, etc.).

### 2. Sentiment Scoring
- **VADER (Valence Aware Dictionary and sEntiment Reasoner)** was used to calculate sentiment scores (`pos`, `neu`, `neg`) from the review text.
- **RoBERTa**, a transformer-based language model, was applied to generate sentiment logits for each review. These logits were normalized using softmax to obtain probability-like scores for each class.

### 3. Feature Engineering
- Combined VADER and RoBERTa scores to form a 6-dimensional feature vector for each review.
- Features were scaled using `StandardScaler` to improve classifier performance.

### 4. Handling Class Imbalance
- Applied **SMOTE (Synthetic Minority Oversampling Technique)** to generate synthetic examples for underrepresented classes (neutral and negative), creating a balanced dataset.

### 5. Classification
- Used **Logistic Regression** for final sentiment classification.
- The classifier was trained on the hybrid feature vectors (VADER + RoBERTa).

### 6. Model Evaluation
- Evaluated model on test data using:
  - **Accuracy Score**
  - **Precision, Recall, F1-Score**
  - **Confusion Matrix**
  - **5-Fold Cross-Validation Accuracy**
- Achieved ~97% test accuracy and ~98% average cross-validation accuracy.

### 7. Visualization
- Confusion Matrix to observe misclassifications across classes.
-  ![image](https://github.com/user-attachments/assets/448f0f87-54fa-446e-919b-21275d96153d).

                    
  
- Bar plots comparing average sentiment scores from VADER and RoBERTa.
  ![image](https://github.com/user-attachments/assets/8bbfa6a9-429c-49a9-9713-a62fe749eaa9)
  
- Pairplot to visualize feature distributions and class separability.
 ![image](https://github.com/user-attachments/assets/aefab2b9-8cb8-431b-8760-2e9f10a7fbaa)

---

## Results

- **Test Accuracy:** ~97%
  
  -![image](https://github.com/user-attachments/assets/bd9eb025-4cfb-429b-b93a-3036c6e7e490)

- **5-Fold CV Accuracy:** ~98%
  
  ![image](https://github.com/user-attachments/assets/361cec44-e261-48bb-9f5a-af9eee9c8835)

- Confusion matrix and pairplots visualize class separability and sentiment score distribution.

 

  


---


## License

This project is licensed under the MIT License. See the [LICENSE](https://github.com/Jaycee-404/Hybrid-Sentiment-Analysis-using-RoBERTA-and-VADAR/blob/main/LICENSE) file for details.
