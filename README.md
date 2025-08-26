# Future_Intern_DS_03
This repository contain the jupyter notebook file for sentiment analysis of school students.
# Student Feedback Sentiment Analysis (Project 2 – Internship)

Analyze student feedback across multiple academic categories using **TextBlob** sentiment analysis, visualize distributions, and explore relationships between numeric ratings and sentiment.

> **Tech stack:** Python, pandas, TextBlob, matplotlib, seaborn, WordCloud.


## Project Overview
This project loads a structured Excel dataset of student feedback, computes **sentiment scores and labels** per category, summarizes distributions, generates a **word cloud** of common terms, and visualizes **numeric rating vs. sentiment** relationships and a **correlation heatmap**.

**Categories analyzed**  
- Teaching, Course Content, Examination, Lab Work, Library Facilities, Extracurriculars.



## 🗂️ Data
- **Source file:** `finalDataset0.2.xlsx`  
- **Sheet:** `finalDataset0.2`  
- **Key mapping used for sentiment text columns:**
  ```python
  columns_map = {
      'teaching': 'teaching.1',
      'coursecontent': 'coursecontent.1',
      'examination': 'Examination',
      'labwork': 'labwork.1',
      'library_facilities': 'library_facilities',
      'extracurricular': 'extracurricular.1'
  }
  ```



## Features
- Sentiment score (polarity) and label (**Positive / Neutral / Negative**) for each category using **TextBlob**.  
- **Stacked bar charts** of sentiment distribution by category.  
- **Word cloud** to highlight frequent terms in feedback.  
- **Crosstabs** of *numeric ratings vs. sentiment* for each category with visualizations.  
- **Correlation heatmap** between numeric ratings and sentiment scores.  



## 🔎 Key Results (sample)
**Sentiment distribution across categories (percent):**  
```
teaching.1           Negative 7.03 | Neutral 4.32 | Positive 88.65
coursecontent.1      Negative 7.57 | Neutral 18.38 | Positive 74.05
Examination          Negative 8.65 | Neutral 10.27 | Positive 81.08
labwork.1            Negative 11.35 | Neutral 12.43 | Positive 76.22
library_facilities   Negative 0.00 | Neutral 100.00 | Positive 0.00
extracurricular.1    Negative 4.32 | Neutral 14.05 | Positive 81.62
```

> Example insight: **Teaching** and **Examination** feedback skew strongly positive; **Library Facilities** feedback is entirely neutral in this dataset (likely short/ambiguous text), suggesting either limited opinionated text or data quality quirks.



## Project Structure

.
├─ data/
│  └─ finalDataset0.2.xlsx
├─ notebooks/
│  └─ sentiment_analysis.ipynb
├─ src/
│  └─ sentiment_pipeline.py   # (optional script version)
├─ outputs/
│  ├─ sentiment_distribution.png
│  ├─ wordcloud.png
│  ├─ crosstab_<category>.png
│  └─ correlation_heatmap.png
├─ requirements.txt
└─ README.md
```
*(Adjust to match your repo; filenames reflect the workflow in your PDF.)*

---

## ⚙️ Setup & Installation
```bash
# 1) Create & activate a virtual environment (optional but recommended)
python -m venv .venv
# Windows
.venv\Scripts\activate
# macOS/Linux
source .venv/bin/activate

# 2) Install dependencies
pip install -r requirements.txt
```

**requirements.txt (suggested)**
```
pandas
textblob
matplotlib
seaborn
wordcloud
openpyxl
```

---

## 🚀 How to Run

### Option A: Jupyter Notebook
1. Place `finalDataset0.2.xlsx` in `data/`.
2. Open `notebooks/sentiment_analysis.ipynb`.
3. Run all cells to generate summary tables and plots.

### Option B: Python Script (if you add `src/sentiment_pipeline.py`)
```bash
python src/sentiment_pipeline.py --input data/finalDataset0.2.xlsx --sheet finalDataset0.2 --out outputs/
```

---

## 📊 Outputs
- **Sentiment Distribution (stacked bars)** per category  
- **Word Cloud** of frequent terms in feedback  
- **Numeric Ratings vs Sentiment** crosstabs & stacked bars for each category  
- **Correlation Heatmap** between numeric ratings and sentiment scores  
All plots are saved to `outputs/`.  

---

## 🧠 Methods
- **Sentiment scoring:** `TextBlob(text).sentiment.polarity`  
- **Labeling rule:** `score > 0 → Positive`, `score == 0 → Neutral`, `score < 0 → Negative`  
- **Aggregation:** `value_counts(normalize=True) * 100` for percentage distributions  
- **Visualization:** `matplotlib`/`seaborn` for bars & heatmap; `WordCloud` for term frequency.  

---

## 📈 Example Usage Snippets
```python
from textblob import TextBlob

def get_sentiment_label(score):
    if score > 0: return "Positive"
    if score < 0: return "Negative"
    return "Neutral"


## 🔭 Next Steps
- Replace TextBlob with **VADER** or **transformer-based** sentiment models for domain nuance.
- Clean/augment **Library Facilities** text to avoid all-neutral outputs.
- Add **confidence intervals** and **statistical tests** (e.g., χ² on crosstabs).
- Build a lightweight **Streamlit** dashboard to explore results interactively.

## 🤝 Contributing
Pull requests are welcome! For major changes, please open an issue to discuss what you’d like to change.

