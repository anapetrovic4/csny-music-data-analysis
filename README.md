# CSNY Music Data Collection and Analysis

A multi-source music data pipeline combining Spotify, AllMusic, and Wikipedia data to analyse the discography, popularity, audio features, genres, and mood profiles of Crosby, Stills, Nash & Young and their related solo projects.

## Project Overview

This project collects, cleans, and integrates music data from three online sources:

- **Spotify** — popularity and audio features
- **AllMusic** — genres, styles, moods, themes, and credits
- **Wikipedia** — artist, album, and release information

The final dataset is used for a case study of Crosby, Stills, Nash & Young (CSNY), including their group and solo work.

## Objectives

- Build a reusable multi-source music dataset.
- Standardize artist, album, and track information.
- Analyze the evolution of genres and styles.
- Compare the popularity of solo and group projects.
- Examine relationships between Spotify audio features and popularity.
- Compare moods and themes across CSNY members.

## Data Pipeline

```text
Spotify ─────┐
AllMusic ────┼──> Cleaning and standardization ──> Dataset merging ──> Final dataset ──> EDA
Wikipedia ───┘
```
## Dataset

Each row in the final dataset represents one track, enriched with album-level metadata and Spotify audio features.

| Data group | Example features |
|---|---|
| Track information | track, artist, album, release date |
| Album metadata | album type, recording period, recording location |
| Music categories | genres, styles, moods, themes |
| Credits | composers, producers, vocals |
| Spotify metrics | popularity, danceability, energy, loudness |
| Additional audio features | acousticness, valence, tempo, instrumentalness |

## Research Questions

1. How did the dominant genres and styles change throughout the artists' careers?
2. Did the addition of Neil Young substantially increase the band's popularity?
3. Which solo and group projects achieved the highest average popularity?
4. Are Spotify audio features associated with track popularity?
5. How do moods and themes differ between the members' solo and group work?

## Key Findings

- Rock remained the dominant genre, although individual artists explored a broader range of styles.
- CSNY had only slightly higher average popularity than CSN.
- Neil Young achieved the highest average popularity among the individual members.
- Spotify audio features showed weak correlations with track popularity.
- Solo and group projects differed in their dominant moods and themes.
- Neil Young had the most diverse mood profile among the analyzed artists.



# Project Structure

The repository is organized as follows:
```
.
├── analysis/                     # Analysis notebooks
│   ├── descriptive_analysis.ipynb
│   └── exploratory_analysis.ipynb
│
├── data/                         # All datasets
│   ├── AllMusic/
│   │   ├── raw/
│   │   ├── v2/
│   │   └── v3/
│   │
│   ├── Spotify/
│   │   ├── raw/
│   │   ├── v2/
│   │   └── v3/
│   │
│   ├── Wikipedia/
│   │   ├── raw/
│   │   ├── v2/
│   │   └── v3/
│   │
│   ├── combined/                 # Combined datasets
│   │   ├── allmusic-combined/
│   │   ├── wikipedia-combined/
│   │   ├── spotify-combined/
│   │   └── allmusic-wikipedia-combined/
│   │
│   └── final/                    # Final dataset
│       └── csny/
│
├── scripts/                      # Python scripts
│   ├── allmusic/
│   │   ├── data_cleaning.py
│   │   ├── data_cleaning_2.py
│   │   └── web_scraping.py
│   │
│   ├── spotify/
│   │   ├── data_cleaning.py
│   │   ├── data_cleaning_2.py
│   │   └── data_extraction.py
│   │
│   ├── wikipedia/
│   │   ├── data_cleaning.py
│   │   └── web_scraping.py
│   │
│   └── merging_and_cleaning/
│       └── final_dataset_merging_and_cleaning.py
│
└── README.md
```

## Technologies

- Python
- pandas
- NumPy
- Matplotlib
- Seaborn
- Beautiful Soup
- Spotify Web API
- Jupyter Notebook

## Detailed Description

### Scripts
- **allmusic**
  - `data_cleaning.py`, `data_cleaning_2.py` – cleaning procedures for AllMusic data  
  - `web_scraping.py` – extraction of raw data from AllMusic  
- **spotify**
  - `data_extraction.py` – data extraction from Spotify  
  - `data_cleaning.py`, `data_cleaning_2.py` – cleaning procedures for Spotify data  
- **wikipedia**
  - `web_scraping.py` – extraction of raw data from Wikipedia  
  - `data_cleaning.py` – cleaning procedures for Wikipedia data  
- **merging_and_cleaning**
  - `final_dataset_merging_and_cleaning.py` – merging of datasets from all sources and final cleaning  

---

### Analysis
- **descriptive_analysis.ipynb** – descriptive statistics as an introduction to exploratory analysis  
- **exploratory_analysis.ipynb** – exploratory analysis applied to the *csny* dataset  

---

### Data
- **AllMusic Datasets**: raw, v2, v3  
- **Spotify Datasets**: raw, v2, v3  
- **Wikipedia Datasets**: raw, v2, v3  
- **combined**  
  - *allmusic-combined*  
  - *wikipedia-combined*  
  - *spotify-combined*  
  - *allmusic-wikipedia-combined*  
- **final**  
  - Dataset created by combining *allmusic-wikipedia-combined* and *spotify-combined*  
  - Includes the *csny* dataset  

---
# How to Run

To reproduce the workflow, follow these steps:

1. **Download the repository folder** to your local machine.
2. **Run the web scraping scripts** for all three data sources:
   - `scripts/spotify/data_extraction.py`
   - `scripts/allmusic/web_scraping.py`
   - `scripts/wikipedia/web_scraping.py`
3. **Run the cleaning scripts** to process the scraped data:
   - `scripts/spotify/data_cleaning.py` and `data_cleaning_2.py`
   - `scripts/allmusic/data_cleaning.py` and `data_cleaning_2.py`
   - `scripts/wikipedia/data_cleaning.py`
4. **Run the final merging and cleaning script** to combine the datasets:
   - `scripts/merging_and_cleaning/final_dataset_merging_and_cleaning.py`
5. **Perform the analysis** using:
   - `analysis/descriptive_analysis.ipynb`
   - `analysis/exploratory_analysis.ipynb`
  
## Limitations

- Spotify popularity scores may change over time.
- Metadata naming conventions differ across data sources.
- AllMusic mood and theme categories are subjective.
- Missing metadata may affect comparisons between artists.
- Correlation does not imply that an audio feature causes popularity.
- The CSNY case study is not representative of the entire music industry.

## Future Work

- Expand the dataset to additional bands and artists.
- Automate the complete ETL pipeline.
- Introduce statistical tests and confidence intervals.
- Develop an interactive dashboard.
- Build a music similarity or recommendation model.

## Author

**Ana Petrović**

Master's Programme in Information Engineering  
University of Belgrade — Faculty of Organizational Sciences
