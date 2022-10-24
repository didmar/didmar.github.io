---
layout: page
title: Social media analysis pipeline
img: assets/img/hcore.png
importance: 2
category: work
---

Stack: Python, [Prefect](https://www.prefect.io), [MongoDB](https://www.mongodb.com/), [ElasticSearch](https://www.elastic.co/elasticsearch/), [BigQuery](https://cloud.google.com/bigquery), [FastAPI](https://fastapi.tiangolo.com)

The backbone of [Heuritech](https://www.heuritech.com)'s product is a data pipeline processing 3M+ social media posts/day.
It involves web crawling, Deep Learning-based image analysis and interaction with manual labeling processes.
I led its development of it over the years, making it scale to new data sources and new product offers.

The pipeline was built on a task queue system and orchestrated by [Prefect](https://www.prefect.io), a Python-based workflow engine.
The whole ETL process can be summarized like so:
- **Extract**: Gather social media posts from various sources (Instagram, Weibo...) as well as their images and meta-data about the author (for example their location).
- **Transform**: Apply our image and text analysis models on the raw data, to enrich it with fashion attributes: brand, color, style, etc. 
- **Load**: Data that is relevant to our product is inserted in [ElasticSearch](https://www.elastic.co/elasticsearch/), where it will be easily searchable across many attributes.

Intermediate results are stored in [MongoDB](https://www.mongodb.com/), a document-oriented NoSQL database that is very convenient for evolving the schema over time.
However, scaling MongoDB to keep the historical data implies a lot of operational work and cost, so we move the historical data to [BigQuery](https://cloud.google.com/bigquery), a managed data warehouse from Google Cloud, using Parquet files in GCS buckets.

Finally, data is exposed as a REST API, using [FastAPI](https://fastapi.tiangolo.com), a modern Python web framework.

# Challenges

Although the steps I described may seem pretty straightforward, things are more complex in reality as there are different use cases.
For example, in some cases, we need to check the quality of the predicted attributes before it ends up in the product. This implies going through an additional step with our custom labeling interface.
In other cases, we only care about the overall tendencies and checking each post would be a loss of time and money.
Some image analysis models are more computationally demanding than others and we try not to use them when it is not necessary, which implies different parametrization.
Finally, sometimes we need to reanalyze old posts to benefit from improved models, which implies skipping the extraction part.
The pipeline was designed as a monolithic process, which is justified by the fact that there are a lot of similarities between use cases.
But keeping track of all these different use cases required a lot of care and end-to-end testing.

Making the data accessible was also challenging.
While we designed everything based on what the clients wanted to see in the product, we did not plan on making it easy to use internally for data scientists.
As we developed more reports and customized analyses, we had to find ways to make all the raw data easily accessible.
The solution was found in a trade-off between using ElasticSearch for fast and easy access to the more recent data, and BigQuery for extracting relevant historical data.