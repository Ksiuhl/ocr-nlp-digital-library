# OCR + NLP Digital Library

An AI-powered digital library system for processing scanned documents using OCR, image preprocessing, LLM-based text correction, summarization, and semantic document clustering.

## Overview

This project was developed as my final-year capstone project for the BSc in Applied Data Science at Hong Kong Shue Yan University.

The system aims to convert scanned library and archival materials into searchable and structured digital records. It combines computer vision, OCR, natural language processing, and web technologies in a complete document-processing workflow.

## Key Features

- Image preprocessing using OpenCV
- OCR processing using DeepSeek OCR
- Tesseract OCR fallback for English and Chinese documents
- OCR text correction using Qwen
- Automatic title and author generation
- Document summarization
- Semantic similarity analysis
- Automatic document clustering
- Multi-image document upload
- OCR result and metadata editing
- PostgreSQL document storage
- Web-based document management interface

## System Workflow

1. User uploads scanned document images
2. Images are preprocessed using OpenCV
3. DeepSeek OCR extracts text from the document
4. Tesseract is used as a fallback when required
5. Qwen improves OCR output and generates metadata
6. NLP processing generates summaries
7. Semantic embeddings are used for document similarity and clustering
8. Results are displayed in the web interface
9. Processed documents are stored in PostgreSQL

## Technologies

### AI / Machine Learning
- DeepSeek OCR
- Qwen
- Tesseract OCR
- Sentence Transformers
- Transformers

### Computer Vision
- OpenCV
- CLAHE
- Adaptive Thresholding
- Morphological Processing

### Backend
- Python
- Flask
- PostgreSQL
- Prisma

### Frontend
- Next.js
- React
- TypeScript

### Development Environment
- Google Colab
- Jupyter Notebook

## Architecture

```text
Scanned Images
      ↓
Image Preprocessing
      ↓
DeepSeek OCR
      ↓
Tesseract Fallback
      ↓
OCR Text
      ↓
Qwen Text Correction
      ↓
Metadata + Summary Generation
      ↓
Semantic Embeddings
      ↓
Document Clustering
      ↓
Next.js Web Application
      ↓
PostgreSQL Database
