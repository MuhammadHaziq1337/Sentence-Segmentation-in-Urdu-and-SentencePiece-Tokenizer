# Sentence Segmentation in Urdu and SentencePiece Tokenizer

## Introduction

This project implements and practices fundamental text processing techniques in NLP for the **Urdu language**. Sentence segmentation in Urdu is challenging due to issues like **space insertion** and **space omission**, making traditional approaches less effective. 

The goals of this project are:
1. Implement Urdu Sentence Segmentation.
2. Build a custom **SentencePiece Tokenizer** for Urdu sentences.
3. Evaluate segmentation and tokenization techniques.

A sample Urdu corpus, `urdu-corpus.txt`, is provided as input for these tasks.

---

## Key Challenges

- Identifying patterns in Urdu text.
- Recognizing sentence-ending words.
- Handling various punctuation marks specific to Urdu.
- Writing functions for segmentation, tokenization, and performance evaluation.

---

## Implementation

### 1. Loading Data
The dataset is loaded from a text file and preprocessed for segmentation. Below is a snippet of the text:
```python
Original text (first 500 characters):
### 2. Sentence Segmentation
#### Approach:
- Identified common **sentence-ending patterns** such as words like "ہے", "تھا", "تھی", and punctuation like "۔", "؟", and "!". 
- Used **regular expressions** to split the text into sentences based on these patterns.
- Accounted for cases like nested punctuation and quotes.

#### Example Output:
Input:بے چاری عوام چونکہ ہمیشہ سے دھوکہ کھانے کی عادی رہی ہے اس لئے ‘‘تبدیلی سرکار’’ کی چکنی چپڑی باتوں میں آگئی ...

Output:بے چاری عوام چونکہ ہمیشہ سے دھوکہ کھانے کی عادی رہی ہے۔ اس لئے ”تبدیلی سرکار“ کی چکنی چپڑی باتوں میں آگئی
```
---
### 3. SentencePiece Tokenizer
#### Workflow:
- Built a custom **SentencePiece model** for Urdu text. The tokenizer was trained on segmented sentences to handle subword tokenization effectively.
- Implemented encoding and decoding functions to convert text into subwords and reconstruct sentences.

#### Example:
```python
# Encode and decode a sample text
encoded = sp_model.encode("بے چاری عوام چونکہ ہمیشہ سے دھوکہ کھانے کی عادی رہی ہے۔")
decoded = sp_model.decode(encoded)

print("Encoded:", encoded)
print("Decoded:", decoded)
```
بے چاری عوام چونکہ ہمیشہ سے دھوکہ کھانے کی عادی رہی ہے اس لئے ...
