# Content_structure_to_seo_score
Pipeline for analyzing Arabic SEO content structure and calculating SEO scores with Power BI-ready outputs.
```markdown
# Arabic SEO Content Brief Pipeline

A comprehensive pipeline for generating InLinks-style content briefs for Arabic pages with Power BI-ready outputs.

## Features
- Arabic NLP processing with UTF-8 support
- SERP analysis via DataForSEO API
- Entity/topic extraction using DeepSeek API
- Keyword clustering and intent inference
- SEO scoring with competitive analysis
- Power BI-ready CSV outputs

## Installation

1. Create virtual environment:
```bash
py -3.11 -m venv .venv
```

2. Activate environment:
```bash
.venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Setup environment:
```bash
copy .env.example .env
# Edit .env with your API credentials
```

## Usage

### Initialize project with your CSV:
```bash
python -m src.cli init --source "D:\Content analysis\content-inputs.csv"
```

### Run full pipeline:
```bash
python -m src.cli run --input "data/input/content-inputs.csv" --device desktop --topk 10
```

### Run individual components:
```bash
# SERP analysis only
python -m src.cli serp --input "data/input/content-inputs.csv"

# NLP analysis only
python -m src.cli nlp --input "data/input/content-inputs.csv"
```

## Output Files

All outputs are UTF-8 encoded CSVs in `data/output/`:

- `pages_master.csv` - Main metrics and scores
- `topics_analysis.csv` - Entity/topic gaps
- `serp_analysis.csv` - Competitor analysis
- `keyword_clusters.csv` - Keyword groupings
- `questions.csv` - Related questions
- `content_structure.csv` - Content structure metrics

## SEO Score Formula

```
SEO_Score = 0.40 * Topics_Coverage + 
            0.20 * Keyword_Coverage + 
            0.15 * Structure_Score + 
            0.15 * Intent_Match + 
            0.10 * Readability_Score
```

## Power BI Integration

1. Open Power BI Desktop
2. Get Data → Text/CSV
3. Select output CSVs
4. Ensure UTF-8 encoding is selected
5. Load and create relationships on `url` and `target_keyword` fields
