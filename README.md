# San Jae Mate
### Medical Facility Review Collection and Summarization

## Overview

San Jae Mate is an undergraduate project that explores how publicly available medical facility information and online reviews can be combined to make healthcare-related information easier to access.

The project uses a public directory of medical facilities designated under South Korea's Industrial Accident Compensation Insurance system, collects publicly visible visitor reviews from Kakao Map, and integrates the OpenAI API to generate concise Korean-language summaries.

The goal is to demonstrate a workflow connecting **public data, web automation, text extraction, and LLM-based summarization**.

## Technologies

- **Python** — Data processing and application logic
- **Pandas** — Loading and filtering medical facility data
- **Selenium** — Browser automation and navigation
- **BeautifulSoup** — HTML parsing and review text extraction
- **OpenAI API** — LLM-based review summarization
- **Jupyter Notebook** — Exploratory development and documentation

## Data Source

The project uses a public dataset published by the Korea Workers' Compensation & Welfare Service (COMWEL), containing information about designated medical facilities.

The original notebook was developed using a dataset snapshot dated December 31, 2022.

Facility names and addresses are used to search for corresponding listings on Kakao Map. Search results must be verified before collecting reviews.

The original dataset is not included in this repository.

## Implementation

### 1. Medical Facility Selection

The public facility directory is loaded using Pandas. A medical facility is selected, and its name and address are used to construct a search query.

### 2. Review Collection

Selenium is used to navigate Kakao Map and access the verified facility's review page.

BeautifulSoup extracts review text from the loaded HTML content. The collection logic also expands truncated reviews to retrieve their full visible text.

The current implementation processes reviews loaded in the browser. It does not guarantee collection of every review associated with a facility.

### 3. LLM-Based Summarization

The project provides an optional summarization function using the OpenAI API.

The function is designed to identify recurring positive and negative themes in the collected review text and produce a concise Korean-language summary.

Reviews are treated as subjective, unverified accounts rather than established medical facts.

## How to Run

### Requirements

- Python 3
- Google Chrome
- Jupyter Notebook
- Pandas, Selenium, BeautifulSoup4, and OpenAI Python SDK

Install the required packages:

```bash
pip install pandas selenium beautifulsoup4 openai
```

### Execution

1. Download the public medical facility dataset and place the CSV file in the notebook directory.
2. Open `medical_facility_reviews.ipynb` in Jupyter Notebook.
3. Select a medical facility from the dataset.
4. Run the Selenium search and verify the facility listing using its name and address.
5. Navigate to the corresponding review page and execute the review extraction code.
6. Optionally configure `OPENAI_API_KEY` in your local environment to use the summarization function.

The OpenAI API call is disabled by default. API credentials must not be committed to the repository.

## Limitations

- **Website dependency:** The project depends on Kakao Map's HTML structure, which may change over time.
- **Incomplete coverage:** Review collection is limited to content currently loaded in the browser. Full pagination is not implemented.
- **Review reliability:** Online reviews are subjective and may not represent the overall quality of a medical facility.
- **LLM limitations:** Generated summaries may omit context or misinterpret reviewer statements.
- **Privacy:** Reviews may contain personal or sensitive information and should be reviewed before external processing or publication.
- **Data collection restrictions:** Automated collection must comply with applicable website terms and access restrictions.

## Project Background

This project was originally developed as an undergraduate exploration of web scraping and natural language processing applications.

The notebook was subsequently revised to improve code organization, browser compatibility, review extraction, API credential handling, and documentation.

It is intended as a **technical prototype rather than a production-ready medical information service**.
