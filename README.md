# Moroccan Financial Statements Extraction using Vision-Language Models

Automated financial statement extraction from scanned Moroccan balance sheets using **Qwen2.5-VL, OpenCV, and Python**.

This project explores the use of Vision-Language Models (VLMs) to extract structured accounting information from PDF financial documents, reconstruct financial tables, validate accounting consistency, and export the extracted data into CSV files.

## 1. Project Overview

Financial statements often contain complex tables, scanned content, and inconsistent layouts, making traditional text extraction difficult.

This project implements a hybrid **Computer Vision + Vision-Language Model** pipeline for extracting Moroccan financial statements, specifically:

- **ACTIF (Assets):** Gross value, depreciation/provisions, net value for the current year (N), and net value for the previous year (N−1).
- **PASSIF (Liabilities and Equity):** Financial amounts for the current year (N) and previous year (N−1).

The objective is to transform financial documents into structured, machine-readable datasets while preserving the original accounting information.

## 2. Technologies Used

| Technology | Purpose |
|---|---|
| Python | Data processing and pipeline implementation |
| Qwen2.5-VL-3B-Instruct | Vision-language information extraction |
| Hugging Face Transformers | Model loading and inference |
| PyTorch | Deep learning inference |
| OpenCV | Table structure detection and image preprocessing |
| Pillow | Image processing and cropping |
| Pandas | Data reconstruction and manipulation |
| JSON | Structured extraction format |
| Google Kaggle | GPU-enabled notebook execution |

## 3. Extraction Pipeline

The project follows these main stages:

**Step 1 — PDF Preprocessing**

Convert PDF pages into images and identify the ACTIF and PASSIF financial statements.

**Step 2 — Table Structure Detection**

Use OpenCV to detect horizontal boundaries, identify columns, and determine the positions of accounting rows.

**Step 3 — Image Segmentation**

Divide large financial tables into smaller image blocks to improve extraction reliability and reduce model generation errors.

**Step 4 — VLM-Based Extraction**

Use Qwen2.5-VL to interpret financial statement images and extract:

- Accounting labels
- Row identifiers
- Financial amounts
- Missing or empty cells

**Step 5 — JSON Parsing and Reconstruction**

Convert model responses into structured JSON objects and reconstruct ACTIF and PASSIF tables using Pandas DataFrames.

**Step 6 — Accounting Validation**

Apply automated checks to verify financial consistency, including:

- Gross value − depreciation = net value
- Subtotal consistency
- Financial statement totals
- Total ACTIF = Total PASSIF for both accounting periods

**Step 7 — CSV Export**

Export the validated financial statements into two structured CSV files.

## 4. Results

The pipeline was evaluated on a Moroccan financial statement PDF containing ACTIF and PASSIF tables.

