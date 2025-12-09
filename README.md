# 📰 InfoNewsHarvester – Serverless News Scraping & Analysis Pipeline

This project implements a Serverless Data Engineering Pipeline designed to extract, process, and analyze news data from multiple web sources.It integrates AWS Lambda for computing, S3 for storage, and services like AWS Glue and Athena to structure the data.The final output is a consolidated CSV dataset ready for querying in a Jupyter Notebook, enabling machine learning predictions and trend analysis.

## ☁️ Introduction to Serverless ETL & Cloud Computing

Cloud Computing allows for on-demand delivery of IT resources over the Internet. Within this project, we utilize a Serverless architecture to build an efficient ETL (Extract, Transform, Load) pipeline:

- **Extract:** Lambda functions trigger to scrape raw HTML data from target news websites.
- **Transform:** Data is cleaned, parsed, and structured into a usable format.
- **Load:** The processed data is stored in a Data Lake (S3) and cataloged (Glue) for analysis.

In this project, the InfoNewsHarvester acts as an automated data agent:

Perception → Scripts visit web pages to identify headlines and content.
Processing → Raw text is converted into structured data (Dates, Titles, Bodies).
Action → Data is consolidated into CSV format for predictive modeling.

This structure allows for a scalable, cost-effective system that requires no server management.

## 🚀 Features

- ☁️ **AWS Serverless Architecture:** Built entirely on AWS Lambda, S3, Glue, and Athena.
- 🕷️ **Multi-Source Scraping:** Extracts news from two distinct websites simultaneously.
- 🗂️ **Structured Data Storage:** Saves raw and processed data in Amazon S3 buckets.
- 🔢 **Sequential Processing:** Utilizes four distinct Lambda functions (I, II, III, IV) for modular execution.
- 📊 **Data Cataloging:** Integrated with AWS Glue and Athena for SQL-like querying.
- 📉 **Machine Learning Ready:** Generates a clean CSV format optimized for Jupyter Notebooks and predictive models.
- 🤖 **Automated Workflow:** From raw HTML to analytical dataset without manual intervention.

## 💻 Code Workflow

The project is divided into four main Lambda functions, identified by Roman numerals, representing the stages of the pipeline:

### Lambda I & Lambda II (Extraction)

- **Role:** The Harvesters.
- **Functionality:**
  - Connect to the two specific target news websites.
  - Scrape the HTML content (headlines, dates, article bodies).
  - Store the raw data directly into an S3 "Landing Zone" bucket.

### Lambda III (Transformation)

- **Role:** The Processor.
- **Functionality:**
  - Triggered after extraction.
  - Cleans the raw text (removing HTML tags, formatting dates).
  - Normalizes the data structure to ensure consistency between the two different sources.
  - Moves the cleaned data to a "Processed" S3 bucket.

### Lambda IV (Loading & Aggregation)

- **Role:** The Loader.
- **Functionality:**
  - Aggregates processed files.
  - Interfaces with AWS Glue to update the Data Catalog.
  - Prepares the final CSV output accessible via Amazon Athena or direct download for analysis.

## 🧩 How It Works

**Trigger:** The pipeline is initiated (via EventBridge schedule or manual trigger).

**Scraping Phase:** Lambda I and Lambda II execute in parallel to fetch the latest news from their respective sources.

**Storage:** Raw data is saved to S3.

**Processing Phase:** Lambda III reads the raw S3 data, applies text cleaning, and structures the information.

**Cataloging:** Lambda IV ensures the data is recognized by the AWS Glue Crawler.

**Analysis:**

- The user opens the provided Jupyter Notebook.
- Connects to the S3 bucket or Athena.
- Loads the CSV data to train Prediction Models (e.g., trend forecasting or sentiment analysis).

## 🧠 Data Flow & Analysis

After the Lambda functions complete their execution, the data flow results in a clean dataset.

### Raw Input (Web):
Unstructured HTML, mixed formatting, advertisements, variable date formats.

### Transformation (Lambda III):
Cleaning rules apply:
- Strip HTML tags.
- Normalize date to YYYY-MM-DD.
- Remove empty rows.Final
- 
### Output (CSV/Athena):

| Titular | Categoria | predicted_categoria |
| :--- | :--- | :--- |
| Abriendo mercados: transformando la economia regional | Contenido patrocinado | Contenido patrocinado |
| Aviajar colombia s.a.s. denuncia uso inadecuado de su nombre | Contenido patrocinado | Contenido patrocinado |
| Siga en vivo la ceremonia de los premios portafolio 2024 | Economia | Economia |
| Vea y descargue aqui la edicion digital de portafolio fin de semana | Economia | Opinion/analisis |
| Vea y descargue aqui la edicion digital de portafolio fin de semana | Economia | Opinion/analisis |

This standardized format allows the Jupyter Notebook to immediately begin Feature Engineering and Model Training.

## 🔧 Tech Stack & Requirements

- **Cloud Provider:** Amazon Web Services (AWS)
- **Compute:** AWS Lambda (Python Runtime)
- **Storage:** Amazon S3 (Simple Storage Service)
- **ETL & Query:** AWS Glue, Amazon Athena
- **Local Analysis:** Jupyter Notebook / Python Pandas
- **Libraries:** boto3, requests, pandas, beautifulsoup4 (or selenium depending on implementation)


## 📊 Future Improvements

- 🔄 **Sentiment Analysis:** Integrate AWS Comprehend to score the sentiment of news articles automatically.
- 📈 **Dashboarding:** Connect Amazon QuickSight to visualize news frequency and topics.
- 🤖 **Automated Alerts:** Use SNS to notify when specific keywords appear in the news.
- 🌍 **More Sources:** Scale the scraper to include international news outlets.

## 👨‍💻 Author

Developed by Daniel Bernal

