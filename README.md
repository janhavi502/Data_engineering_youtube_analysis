# YouTube Trending Videos Data Pipeline and Analysis

<img width="1282" alt="image" src="https://github.com/user-attachments/assets/6414ec73-0086-4b15-9d83-7adb9d205326">

This project demonstrates a data architecture for processing and analyzing trending YouTube video data from multiple regions using AWS services. The architecture incorporates a data lake, data processing layers, and analytical access layers.

## Dataset

The dataset used in this project is sourced from Kaggle and contains statistics on daily popular YouTube videos. It includes details such as:
- **Video title**
- **Channel title**
- **Publication time**
- **Tags**
- **Views**
- **Likes and dislikes**
- **Description**
- **Comment count**
- **Category ID** (varies by region)

For more details, see the [dataset on Kaggle](https://www.kaggle.com/datasets/datasnaek/youtube-new).

## Architecture Overview

The data pipeline is designed with the following components:

### Data Lake
- **Landing Area**: Raw data from the Kaggle dataset is stored in S3 buckets for each region.
- **Cleansed / Enriched**: Data is transformed, cleaned, and enriched using AWS Glue.
- **Analytics / Reporting**: Processed data is stored for analytical queries and reporting.

### Data Processing
- **AWS Glue**: Used for data cataloging, classification, and ETL (Extract, Transform, Load) tasks.
- **AWS Lambda**: Additional processing tasks or event-driven operations.

### Data Flow
1. **Source Systems**: Data ingestion starts with the YouTube dataset files stored locally, which are then uploaded to the S3 bucket using the S3 API.
2. **Bulk Data Upload**: Bulk data is loaded into the Landing Area in the data lake.
3. **Data Processing**: AWS Glue and AWS Lambda process and transform the data to prepare it for analysis.
4. **Data Catalogue & Classification**: AWS Glue Data Catalog is used to classify and catalog the data for easy access.
5. **Analytical Data Access**: Data can be queried using AWS Athena or loaded into Redshift (optional) for more complex analysis.

### Target Systems
- **AWS Athena**: Query the processed data in the data lake.
- **Redshift (Optional)**: Data warehouse for complex analysis.
- **Analytics Tools**: Data visualization and analysis can be performed using tools like:
  - AWS QuickSight
  - Power BI (Optional)
  - Qlik (Optional)
  - Notebooks (Jupyter or similar)

### Monitoring and Alerts
- **AWS CloudWatch**: Used for monitoring and alerting across the pipeline to ensure data integrity and process efficiency.




