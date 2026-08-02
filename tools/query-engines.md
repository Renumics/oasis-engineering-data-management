---
title: Query Engines
description: Analytical query engines for fast interactive analytics on lakehouse tables and Parquet files
type: tool-category
domain: data-storage
tags:
  - query-engine
  - sql
  - olap
  - analytics
  - spark
  - duckdb
---

# 🔍 Query Engines

Analytical query engines that can read directly from lakehouse tables and Parquet files — enabling fast interactive analytics on engineering data without ETL.

| Logo | Name | Description | License |
|------|------|-------------|---------|
| <img src="../logos/spark.png" width="40"/> | [Apache Spark](https://spark.apache.org/) | Unified engine for large-scale batch and streaming data processing. Industry standard for ETL pipelines and distributed analytics on lakehouse data. | Apache 2.0 |
| <img src="../logos/duckdb.png" width="40"/> | [DuckDB](https://duckdb.org/) | In-process OLAP database with zero external dependencies. Reads Parquet, CSV, JSON and Iceberg/Delta directly. Ideal for local engineering data exploration. | MIT |
| <img src="../logos/starrocks.svg" width="40"/> | [StarRocks](https://www.starrocks.io/) | High-performance MPP analytical database for real-time and batch analytics. Supports external catalogs for Iceberg and Delta Lake federation. | Apache 2.0 |
| <img src="../logos/bigquery.png" width="40"/> | [BigQuery](https://cloud.google.com/bigquery) | Google's fully managed, serverless data warehouse with built-in ML and BI. Supports Iceberg tables and external data lake connections. | Proprietary |
| <img src="../logos/athena.png" width="40"/> | [Amazon Athena](https://aws.amazon.com/athena/) | Serverless query service that analyzes data in S3 using SQL. Native support for Parquet, Iceberg and other open formats with pay-per-query pricing. | Proprietary |

## See also

- [Lakehouse Formats](lakehouses.md) — table formats these engines read from
- [Data Catalogues](data-catalogues.md) — catalogs that provide table discovery
- [← Back to overview](../README.md)
