# Automated RFQ Intelligence System

## Overview
The **Automated RFQ Intelligence System** is a lightweight, end-to-end pipeline that converts unstructured RFQ (Request for Quotation) product descriptions into structured, machine-readable data.

The system demonstrates how industrial text data can be cleaned, processed using NLP techniques, and exposed through a REST API for downstream analytics and automation workflows. This project is intentionally scoped as a small, production-inspired build suitable for data-related job applications.

---

## Problem Statement
RFQs in manufacturing and procurement are often shared as free-form text, making them difficult to analyze or automate. Extracting structured attributes such as **material**, **dimensions**, and **quantity** typically requires manual effort.

This project automates that process by transforming unstructured RFQ descriptions into structured JSON output.

---

## Key Features
- Scrapes or loads RFQ-style product descriptions
- Cleans and normalizes unstructured text
- Extracts key RFQ attributes:
  - Material
  - Dimensions
  - Quantity
- Exposes extraction results via a FastAPI REST API
- Lightweight and modular design

---

## Tech Stack
- Python
- BeautifulSoup / Selenium (data extraction)
- Pandas & Regex (text cleaning)
- spaCy or LLM-based extraction (NLP)
- FastAPI (API layer)

---

## Project Structure
automated-rfq-intelligence/
│
├── app/
│ ├── main.py # FastAPI application entry point
│ ├── extractor.py # NLP-based RFQ attribute extraction
│ ├── cleaner.py # Text cleaning and normalization
│ └── schemas.py # Pydantic models
│
├── scraper/
│ └── scrape_sample.py # RFQ scraper or sample data loader
│
├── data/
│ ├── raw_rfqs.json # Raw RFQ descriptions
│ └── processed_rfqs.json # Structured extraction output
│
├── requirements.txt
├── README.md
└── .gitignore


---

## Data Flow
1. RFQ descriptions are scraped from web sources or loaded from sample data
2. Raw text is cleaned and normalized
3. NLP logic extracts structured attributes
4. Results are returned via an API endpoint or saved as JSON

---

## Example RFQ Input
Customer requires 500 aluminum brackets.
Dimensions: 120 x 60 x 10 mm.
Material must be Aluminum 6061.

---

## Example Output
```json
{
  "material": "Aluminum 6061",
  "dimensions": "120 x 60 x 10 mm",
  "quantity": 500
}
```
---

## API Usage

**Run the API

uvicorn app.main:app --reload

---

API Usage
Run the API
uvicorn app.main:app --reload

Extract RFQ Attributes

POST /extract

Request Body

{
  "rfq_text": "Customer requires 500 aluminum brackets..."
}


Response

{
  "material": "Aluminum 6061",
  "dimensions": "120 x 60 x 10 mm",
  "quantity": 500
}
