# Amazon ML Business Entity Resolution

A large-scale Business Entity Resolution project developed for the **Amazon ML Challenge 2026**.

## Overview

The objective of this project was to identify records across multiple noisy business data sources that refer to the same real-world business entity.

The challenge involved three independent sources:

- **Source 1** — deduplicated reference entities
- **Source 2** — noisy business records
- **Source 3** — noisy business records

Each Source 1 entity could match zero, one, or multiple records from Sources 2 and 3.

## Approach

The solution focused on scalable candidate generation and precision-oriented matching.

### 1. Data Normalization
- Lowercasing
- Unicode/accent normalization
- Removal of punctuation
- Whitespace normalization
- Business-name normalization
- Address normalization
- Handling common address abbreviations

### 2. Candidate Generation / Blocking

Multiple blocking strategies were explored to avoid comparing millions of records exhaustively:

- Exact business-name blocking
- Exact-address blocking
- Name-token blocking
- Prefix-based blocking
- Address-number blocking
- Country-aware blocking
- Compact business-name blocking

### 3. Entity Matching

Candidate pairs were evaluated using string similarity features including:

- Business-name similarity
- Token-based name similarity
- Address similarity
- Normalized address similarity
- Country consistency
- Numeric/address overlap

### 4. Precision-Oriented Filtering

Because false matches were particularly costly, strict matching thresholds were evaluated and refined through experiments.

The final experimentation included high-confidence matching rules based on:

- Name similarity
- Normalized address similarity
- Candidate uniqueness
- Address-number consistency

## Scale

The challenge involved millions of records across the three sources, requiring memory-efficient processing and chunked operations in Google Colab.

The pipeline was designed to avoid full pairwise comparison and instead reduce the search space through blocking and candidate generation.

## Technologies

- Python
- Pandas
- Scikit-learn
- RapidFuzz
- Google Colab
- GitHub

## Competition Result

The final achieved leaderboard score was:

**0.228284**

The project involved extensive experimentation with blocking, fuzzy matching, address normalization, precision/recall trade-offs, and memory-efficient processing.

## Notebook

The complete implementation and experimentation are available in:

`Amazon_ML_Challenge.ipynb`
