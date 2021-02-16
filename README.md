# StockMarketDataPipeline

## Overview

The purpose of this project is to provide a public database for stock market analysts to query, analyze, and transform data into actionable insights. The application uses Apache Airflow to kick off jobs(Python ETL scripts) that load data that is stored in JSON and CSV format in a bucket on Amazon S3. The data pipeline utilizes python to read in the data from S3, creates and inserts data into tables hosted on Redshift. The redshift database and tables can be accessed by anyone with appropriate credentials and this is where stock market analysis on the final data can take place. 

#### Technology decisions

Amazon Redshift was chosen as the database host as opposed to another Amazon RDS for this project because Redshift is used primarily for reporting and analytics, whereas Amazon RDS is designed for online-transaction processing (OLTP). OLTP workloads require quickly querying specific information and support for transactions like insert, update, and delete and are best handled by Amazon RDS. Amazon Redshift harnesses the scale and resources of multiple nodes and uses a variety of optimizations to provide order of magnitude improvements over traditional databases for analytic and reporting workloads against very large data sets. Amazon Redshift provides an excellent scale-out option as your data and query complexity grows if you want to prevent your reporting and analytic processing from interfering with the performance of your OLTP workload. Now, with the new Federated Query feature, you can easily query data across your Amazon RDS or Aurora database services with Amazon Redshift.

source: [When would I use Amazon Redshift vs. Amazon RDS?](https://aws.amazon.com/redshift/faqs/#:~:text=Both%20Amazon%20Redshift%20and%20Amazon,primarily%20for%20reporting%20and%20analytics.)


#### **Source Data**
This project draws on historical stock data found on Kaggle. The data consists of daily stock prices for a selection of several thousand stock tickers from NYSE and NASDAQ. Unfortunately, it was not possible to parse the data in a manner that allowed exact decimal calculations, so floating point numbers were provided. You can find the dataset here: https://www.kaggle.com/ehallmar/daily-historical-stock-prices-1970-2018

#### Tools used 
* **Python** is used as one of the programming languases because of its ease-of-use and fexibility 
* **SQL** is used for syntax of the table structure and insertion of records 
* **S3** is used as the data storage for the stock data because of its scalability, and support of multiple file formats 
* **Airflow** is used to orchestrate the steps of the ETL pipeline because of its powerful schedule and monitoring features
* **Redshift** is used to host the data table because of its ease-of-access and ability to handle OLAP for big data 



#### **ERD**
 * Database design is as follows:
![Database Design](https://github.com/sammcint/Data-Engineer-Nanodegree-Projects-Udacity/blob/master/images/Capstone-ERD.png)

