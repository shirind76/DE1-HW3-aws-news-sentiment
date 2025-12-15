
# Sentiment Analysis of Federal Reserve Rate Cut Coverage Using AWS

## Introduction

Following the recent Federal Reserve interest rate cut, financial news outlets and analysts produced extensive coverage through written articles and video commentary. While these sources report on the same economic event, differences may arise in tone, framing, and emotional emphasis.

This project analyzes sentiment across major news outlets and compares written reporting with spoken commentary from YouTube videos. Managed AWS services are used to process multilingual text, transcribe audio content, and extract sentiment indicators in a reproducible data engineering pipeline.

---

## Research Question

How does sentiment differ across major news outlets when covering the same Federal Reserve interest rate decision, and how does sentiment in spoken commentary compare to written reporting?

---

## Data Sources

### News Articles
- CNN
- CNBC
- Reuters
- BBC
- Der Standard (German-language article, translated to English)

### YouTube Videos
- Fox News
- CNN
- CNBC (Fast Money and News segments)
- Reuters (Federal Reserve Chair press conference)

---

## Methodology and Tools

The analysis follows a multi-stage data engineering workflow:

1. News articles are scraped using Python and BeautifulSoup.
2. Non-English content is translated into English using Amazon Translate.
3. YouTube audio files are transcribed using Amazon Transcribe.
4. Sentiment analysis is performed using Amazon Comprehend.
5. Intermediate and final outputs are stored in Amazon S3.
6. Results are aggregated and visualized using pandas and matplotlib.

This approach enables a consistent comparison of sentiment across sources and content formats.

---

## AWS Services Used

- Amazon S3 – cloud storage for raw and processed data
- Amazon Translate – translation of non-English text
- Amazon Comprehend – sentiment analysis
- Amazon Transcribe – speech-to-text transcription

---

## Results and Visualizations

### Average Sentiment: Articles vs YouTube
Written articles tend to exhibit higher neutrality, while YouTube commentary displays stronger positive and negative sentiment.

![Graph 1](output/graphs/graph_1_articles_vs_youtube.png)

---

### Average Sentiment by Source
Differences across outlets suggest varying editorial tone and framing of the same economic event.

![Graph 2](output/graphs/graph_2_sentiment_by_source.png)

---

### Sentiment Distribution
Spoken commentary shows a wider dispersion in sentiment scores, indicating greater emotional variability compared to written articles.

![Graph 3](output/graphs/graph_3_sentiment_distribution.png)

---

### Sentiment Balance by Source
A diverging sentiment chart highlights polarization differences between articles and YouTube videos.

![Graph 4](output/graphs/graph_4_sentiment_diverging_by_source.png)

---

### Sentiment Polarization Index
The polarization index (positive minus negative sentiment) provides a concise ranking of outlets from most pessimistic to most optimistic.

![Graph 5](output/graphs/graph_5_polarization_index.png)

---

## AWS Cost Estimation

The analysis was conducted using AWS free-tier and low-cost managed services. Estimated costs include both final execution and trial-and-error runs during development.

| Service | Approximate Usage | Estimated Cost |
|-------|------------------|----------------|
| Amazon Translate | ~X characters | ~$0.0X |
| Amazon Comprehend | ~X API calls | ~$0.0X |
| Amazon Transcribe | ~X seconds audio | ~$0.0X |
| **Total** |  | **~$0.09** |

Minor variations in sentiment scores may occur due to updates in AWS managed models.

---

## Reproducibility

This project is fully reproducible.

### Requirements
- Python 3.9+
- AWS account with access to:
  - Amazon S3
  - Amazon Translate
  - Amazon Comprehend
  - Amazon Transcribe

### Setup Instructions

```bash
git clone https://github.com/USERNAME/DE1-HW3-aws-news-sentiment.git
cd DE1-HW3-aws-news-sentiment

python3 -m venv venv
source venv/bin/activate

pip install -r requirements.txt

Create a file named accessKeys.csv in the project root with the following columns:
Access key ID,Secret access key
Run the analysis:
python code/DE1_HW_AWS_Script.py
python code/plots.py
Outputs are saved in the output/ directory.

##Conclusion

The results indicate clear differences in sentiment across news outlets and content formats. Spoken commentary on YouTube tends to be more polarized than written articles, while traditionally neutral outlets remain closer to balanced sentiment.

This project demonstrates how AWS managed AI services can be combined into a lightweight, low-cost, and reproducible data engineering pipeline for media sentiment analysis.
