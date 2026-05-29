# Medical Text Preprocessing & Summarization

A Python-based project focused on cleaning, preprocessing, and summarizing complex medical reports using both extractive and abstractive NLP techniques.

## Project Overview

This project provides a robust pipeline for handling medical transcriptions. It includes advanced text cleaning to remove noise (like hospital IDs and dates) while preserving critical medical terminology. Furthermore, it implements three different summarization strategies to condense lengthy medical reports into concise, actionable summaries.

## Key Features

### 1. Advanced Medical Text Preprocessing
*   **Noise Removal:** Automatically strips hospital IDs, patient IDs, dates, and special characters.
*   **Header Cleaning:** Removes standard medical report headers (e.g., SUBJECTIVE, HISTORY, ASSESSMENT) to focus on the core narrative.
*   **Smart Stop-word Handling:** Utilizes NLTK's stop-words but specifically preserves critical medical negations like "no", "not", "without", "normal", and "abnormal".
*   **Intelligent Truncation:** Implements a "smart truncate" function that cuts long reports at sentence boundaries rather than mid-word.

### 2. Multi-Strategy Summarization
The project compares three distinct summarization methods:
*   **Extractive (TF-IDF):** Selects the most important sentences based on term frequency and inverse document frequency.
*   **Extractive (TextRank):** Uses a graph-based ranking algorithm (via the `sumy` library) to identify key sentences.
*   **Abstractive (BART):** Leverages the `facebook/bart-large-cnn` transformer model to generate human-like, paraphrased summaries that capture the essence of the report.

### 3. Performance Evaluation
*   Includes implementation for **ROUGE** score calculation to quantitatively evaluate the quality of generated summaries against the original text.

## Tech Stack

*   **Language:** Python
*   **Data Handling:** `pandas`, `numpy`
*   **NLP Libraries:** `nltk`, `sumy`, `transformers` (Hugging Face)
*   **Deep Learning:** `torch`
*   **Evaluation:** `rouge-score`, `evaluate`

## Project Structure & Logic

### Data Preprocessing Flow
1.  **Loading:** Reads medical reports from a CSV file (`medical_reports.csv`).
2.  **Cleaning:** Applies regex-based cleaning to handle medical-specific noise.
3.  **Tokenization:** Uses NLTK for sentence and word tokenization.
4.  **Refinement:** Handles missing values and applies smart truncation for model compatibility.

### Summarization Implementation
*   **TF-IDF:** Uses `TfidfVectorizer` with bigrams to score and select top sentences.
*   **TextRank:** Employs `PlaintextParser` and `TextRankSummarizer` for graph-based extraction.
*   **BART:** Uses a Hugging Face pipeline with `bart-large-cnn` for high-quality abstractive summarization.

## Example Results

| Method | Summary Preview |
| :--- | :--- |
| **Original** | "this 23 year old white female presents with complaint of allergies..." |
| **TF-IDF** | Focuses on key medical findings and vitals like weight and blood pressure. |
| **TextRank** | Highlights historical context and specific medications. |
| **BART** | Generates a concise, readable paragraph summarizing the patient's condition and history. |

## Installation

```bash
pip install pandas nltk sumy scikit-learn transformers torch sentencepiece rouge-score evaluate
```

## Usage

1.  Ensure your medical data is in a file named `medical_reports.csv` with a `transcription` column.
2.  Run the preprocessing script to clean the data.
3.  Choose your preferred summarization function (`tfidf_summarize`, `textrank_summarize`, or `abstractive_summarize`) to process the reports.

## Author

**Abdulhakim Elsayed (عمو كيمو)**
*Flutter Developer & Computer Engineer*
