# cinema-narrative-shift

**Did short-form video change how films are written?**

TikTok reached mainstream adoption in Western markets around 2018. If shorter
attention spans reshaped mainstream cinema, screenplays after that point should
be measurably more repetitive and thematically narrower.

This project tests that on the text itself: **746 film subtitles, 2003–2025**,
embedded with SBERT (`all-MiniLM-L6-v2`), reduced to a **Topic Diversity Index**
built from pairwise cosine similarity, then compared across a 2018 break.

![Topic Diversity Index by era](outputs/1_distribution_by_era.png)

## Pipeline

The notebooks run in order; each writes what the next one reads.

| | |
|---|---|
| `NB00_collection_preprocessing` | builds the corpus and cleans subtitle text |
| `NB01_sbert_embedding` | sentence embeddings with `all-MiniLM-L6-v2` |
| `NB02_feature_extraction` | cosine similarity → Topic Diversity Index |
| `NB03_eda` | distributions by era, genre, runtime, ratings |
| `NB04_regression` | pre/post-2018 estimation |

Figures land in `outputs/`.

## Running it

```bash
pip install -r requirements.txt
jupyter execute NB0*.ipynb
```

NB00 and NB01 use **PySpark** for the embedding pass and were developed on
Google Colab; on a laptop, expect the SBERT step over 746 files to be the
slow part.

## Data

Subtitles come from OpenSubtitles, film metadata from IMDb. Neither is
redistributed here for licensing reasons — `NB00` documents the collection
step and can rebuild the corpus.

## Context

Final project for **ST446 Distributed Computing for Big Data**, LSE,
Winter Term 2026. Team project: Transpacific Big Data Alliance.

The original write-up is preserved in `README.abstract.bak`.
