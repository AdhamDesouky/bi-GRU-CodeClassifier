
# Code Analysis and Classification with Deep Learning

This repository contains a deep learning-based project for programming language classification using source code snippets. The project implements data preprocessing, tokenization, and a Bidirectional GRU-based neural network model for accurate classification.

---

## Table of Contents

1. [Overview](#overview)
2. [Dataset](#dataset)
3. [Preprocessing Steps](#preprocessing-steps)
4. [Model Architecture](#model-architecture)
5. [Training and Evaluation](#training-and-evaluation)
6. [Requirements](#requirements)
7. [How to Run](#how-to-run)
8. [Results](#results)
9. [Example Code Snippet](#example-code-snippet)

---

## Overview

This project aims to classify programming languages (C, C++, Java, Python) based on their source code snippets. The implemented workflow includes:

- Dataset preparation and oversampling for balanced class distribution.
- Custom tokenization for parsing code snippets.
- Neural network modeling with Bidirectional GRU for sequence classification.

The model achieves high accuracy and can serve as a baseline for similar classification tasks.

---

## Dataset

The dataset used contains labeled programming code snippets for four languages:

- **C**
- **C++**
- **Java**
- **Python**

### Key Statistics
- **Original Samples**: 16,342
- **Balanced Samples per Class (After Oversampling)**: 4,546 for each class.

### Class Distribution Visualization

The class distribution is visualized post-oversampling for uniformity using a bar chart.

---

## Preprocessing Steps

1. **Remove Duplicates**:
   Ensures only unique code snippets are used.
   
2. **Class Balancing**:
   Oversampling is applied to achieve equal representation for each language.
   
3. **Custom Tokenization**:
   A regex-based tokenizer is used to parse identifiers, keywords, operators, and literals.

4. **Token-to-Sequence Conversion**:
   Converts tokens into integer sequences using a vocabulary of the top 10,000 tokens.

5. **Padding**:
   All sequences are padded to a fixed length of 500.

---

## Model Architecture

The deep learning model leverages the following layers:

1. **Input Layer**: Handles padded token sequences.
2. **Embedding Layer**: Maps tokens to dense vectors.
3. **Bidirectional GRU**: Captures sequential relationships in both directions.
4. **Dense Layers with Dropout**: Adds non-linearity and prevents overfitting.
5. **Output Layer**: Outputs class probabilities using softmax.

### Model Summary

| Layer Name            | Output Shape       | Parameters |
|-----------------------|--------------------|------------|
| Input_Layer           | (None, 500)       | 0          |
| Embedding_Layer       | (None, 500, 128)  | 640,000    |
| Bidirectional_GRU     | (None, 256)       | 198,144    |
| Dropout_Layer_1       | (None, 256)       | 0          |
| Dense_Layer           | (None, 64)        | 16,448     |
| Dropout_Layer_2       | (None, 64)        | 0          |
| Output_Layer          | (None, 4)         | 260        |

---

## Training and Evaluation

### Training

The model is trained using:

- Optimizer: **Adam**
- Loss: **Categorical Crossentropy**
- Batch Size: **32**
- Epochs: **10** (with early stopping)

### Metrics

- **Accuracy**
- **Precision**
- **Recall**
- **F1-Score**

### Visualization

- **Training vs. Validation Accuracy**
- **Training vs. Validation Loss**

### Results

| Metric            | Value  |
|--------------------|--------|
| Test Accuracy      | 95.32% |
| Precision (Weighted)| 95%    |
| Recall (Weighted)  | 95%    |
| F1-Score (Weighted)| 95%    |

---

## Requirements

- Python 3.7+
- TensorFlow 2.0+
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Seaborn

Install all dependencies using:
```bash
pip install -r requirements.txt
```

---

## How to Run

1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/code-classification
   ```
   
2. Navigate to the project directory:
   ```bash
   cd code-classification
   ```

3. Place your dataset (`code_snippets_yarab_final.csv`) in the directory.

4. Run the script:
   ```bash
   python code_classification.py
   ```

---

## Results

### Confusion Matrix

A confusion matrix is generated to visualize the classification performance across all four languages.

### Classification Report

Detailed metrics for each class (Precision, Recall, F1-Score) are provided.

---

## Example Code Snippet

```cpp
// Hybrid-like code to confuse the classifier
#include <stdio.h>
#define PI 3.14

template <typename T>
class MyTemplate {
public:
    T data;
    MyTemplate(T val) : data(val) {}
    void display() { std::cout << "Value: " << data << std::endl; }
};

int main() {
    // Python-like list comprehension disguised in a C-style loop
    int arr[] = {1, 2, 3, 4, 5};
    int result[5];
    for (int i = 0; i < 5; i++) {
        result[i] = arr[i] * arr[i];
    }
    printf("Hello, World!\n");
    return 0;
}
```

---

## Acknowledgments

- **Instructor**: Dr. Ghada Khoriba
- **Institution**: Nile University
- **Course**: Machine Intelligence (CSCI417/ECEN425)
