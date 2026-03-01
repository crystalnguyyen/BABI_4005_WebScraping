# Lululemon Reddit Sentiment Analysis
Authour: Crystal Nguyen
Course: BABI 4005
Date: February 29, 2026

---

## Project Overview

This project scrapes posts from the r/lululemon subreddit and performs 
sentiment analysis using VADER to explore whether there is a relationship
between post tone (positive, neutral, or negative) and engagement, measured
by upvote score. The project consists of three Jupyter notebooks covering
data scraping, sentiment analysis, and visualization.

---

## Repo Structure

BABI_4005_WebScraping/
│
├── data/
│   ├── raw_posts.csv               # Scraped Reddit posts (600 posts)
│   └── sentiment_scores.csv        # Posts with VADER sentiment scores
│
├── notebooks/
│   ├── lululemon_sentiment_scraper.ipynb      # Scrapes Reddit posts
│   ├── lululemon_sentiment_analysis.ipynb     # VADER sentiment analysis
│   └── lululemon_sentiment_visualisation.ipynb # Charts and findings
│
├── sentiment_analysis_exports/
│   ├── 01_bar_sentiment.png		# Bar Chart: Average Upvote Score by Sentiment Category
│   ├── 02_boxplot_sentiment.png	# Boxplot: Sentiment Score Distribution by Sentiment Category
│   ├── 03_scatterplot_sentiment.png	# Scatter Plot: Upvote Score vs Sentiment Score
│   └── sentiment_summary_table.csv	# Summarizes different statistics across sentiment categories
└── README.md
---

## How to Run

1. Clone or download this repository
2. Install the required packages
3. Run the notebooks in order:

	- lululemon_sentiment_scraper.ipynb — scrapes and saves raw posts
	- lululemon_sentiment_analysis.ipynb — scores sentiment and saves results
	- lululemon_sentiment_visualisation.ipynb — generates charts and findings

---

## Data Collection

- Source: r/lululemon subreddit via Reddit's public JSON API
- Endpoint: `https://www.reddit.com/r/lululemon/new.json`
- Volume: 600 most recent posts
- Fields Collected: post title, upvote score, body text, URL
- Collection Rate Limit: 0.5 second delay between requests to comply with Reddit API guidelines and prevent IP ban

---

## Methodology
Sentiment analysis was performed using VADER (Valence Aware Dictionary and sEntiment Reasoner).
The Reddit post titles and body text were combined into a single string and scored using VADER's
compound score which ranges from -1 (most negative) to +1 (most positive). Posts were classified
into three categories using VADER's standard thresholds:

1. Positive: >=0.05
2. Negative: <=-0.05
3. Neutral: between -0.05 and 0.05

---

## Key Findings

- 76.5% of posts were classified as positive, reflecting an enthusiastic community in the Lululemon subreddit
- Positive sentiment posts had the highest average upvote score (66.4), compared to neutral (56.6) and negative (43.2)
- The highest upvoted post in the dataset (866 upvotes) was a positive sentiment post
- Negative posts showed the widest spread in sentiment scores, suggesting varying degrees of dissatisfaction

---

## Citations

- r/lululemon. (2026). *r/lululemon* [Online community]. Reddit. https://www.reddit.com/r/lululemon/

- Reddit. (2026). *Reddit API documentation*. https://www.reddit.com/dev/api

## AI Use

- Model: Claude Sonnet 4.6
- AI was used as a learning and development assistant throughout this project. Specifically, it was used to identify different sentiment analysis tools, design the web scraper function, and explain how sentiment scoring works. AI also broke down code to clarify how functions operate, reviewed code and notebook style for best practices, and supported the interpretation of analysis results.
- Sample Queries:
	- "Please write a function to scrape lululemon reddit posts. Make sure to include a delay between requests so you do not overload the server"
	- "Why is VADER better than Textblob? Will it suit my current code?"
	- "Please review my code style and structure and provide feedback on my comments, code, and docstrings"
