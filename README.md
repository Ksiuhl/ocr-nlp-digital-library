# OCR + NLP Digital Library

A final-year Applied Data Science project exploring how OCR, computer vision and lightweight language models can be combined to process scanned documents.

## Overview

This project was developed as my final-year capstone project for the BSc in Applied Data Science at Hong Kong Shue Yan University.

The aim is to turn scanned documents into structured text that can be processed more easily. The current pipeline handles image preprocessing, OCR, OCR quality checking and NLP tasks including summarisation, classification and metadata extraction.

One of the main challenges was that OCR performance varies significantly depending on scan quality. Instead of relying on only one OCR model, I experimented with a hybrid workflow using Tesseract and DeepSeek-OCR.

## Current Pipeline

1. Load a scanned document image
2. Correct image rotation
3. Apply image preprocessing with OpenCV
4. Run Tesseract OCR and calculate its confidence
5. Use DeepSeek-OCR when the Tesseract result is not reliable
6. Detect repetitive or abnormal OCR output
7. Fall back to the Tesseract result if DeepSeek produces unusable output
8. Evaluate OCR text quality
9. Filter text that is too noisy for NLP
10. Use Qwen2.5-0.5B-Instruct for:

* summarisation
* news classification
* title extraction
* author extraction

11. Save the processed results to CSV

## Key Features

* Image preprocessing using OpenCV
* Automatic rotation correction
* CLAHE contrast enhancement
* Otsu thresholding
* Tesseract OCR with confidence scoring
* DeepSeek-OCR integration
* Hybrid OCR selection and fallback
* Repetitive OCR output detection
* OCR text quality estimation
* Filtering of heavily corrupted OCR text
* News article summarisation using Qwen
* Article classification using Qwen
* Title and author extraction
* CSV result generation

## Technologies

### OCR & Computer Vision

* DeepSeek-OCR
* Tesseract OCR
* OpenCV
* CLAHE
* Otsu Thresholding

### NLP / Language Models

* Qwen2.5-0.5B-Instruct
* Hugging Face Transformers
* PyTorch

### Data Processing

* Python
* Pandas
* NumPy

### Development Environment

* Google Colab
* Jupyter Notebook

## OCR Workflow

```text
Scanned Image
      |
      v
Rotation Correction
      |
      v
OpenCV Preprocessing
      |
      v
Tesseract OCR
      |
      v
Confidence / Quality Check
      |
      +---- acceptable ----> Use Tesseract Result
      |
      +---- low confidence
                |
                v
          DeepSeek-OCR
                |
                v
        Repetition Check
          /           \
     accepted       unusable
        |               |
        v               v
   DeepSeek Text   Tesseract Fallback
          \           /
           \         /
             v
          OCR Text
             |
             v
       Text Quality Filter
             |
             v
    Qwen NLP Processing
             |
      +------+------+------+
      |      |      |      |
   Summary Category Title Author
             |
             v
          CSV Output
```

## Repository Structure

```text
ocr-nlp-digital-library/
│
├── README.md
│
└── notebooks/
    └── ocr_nlp_pipeline.ipynb
```

## Notebook

The main notebook contains the OCR and NLP experimentation used during development:

`notebooks/ocr_nlp_pipeline.ipynb`

It includes the complete processing flow from image preprocessing and OCR selection to Qwen-based NLP processing.

## Project Development

The project went through several iterations.

I initially experimented with simpler OCR and rule-based classification methods. As the project developed, I found that OCR output could fail in different ways depending on the quality and structure of the scanned document.

This led me to introduce confidence checking, repetition detection and a hybrid OCR approach rather than depending on a single model.

For NLP processing, I moved from a simple keyword-based classifier to Qwen2.5-0.5B-Instruct, which is used for summarisation, document classification and metadata extraction.

## Future Development

The broader goal of the project is to develop the OCR pipeline into a searchable digital library system.

Areas I plan to continue working on include:

* Semantic document embeddings
* Similarity-based document clustering
* Semantic document search
* Retrieval-based question answering
* Better support for Chinese documents
* Evaluation of OCR accuracy across different document conditions
* Integration with a complete web-based document management interface

## Author

**Siu Ho Lung Kenny**

BSc in Applied Data Science
Hong Kong Shue Yan University
