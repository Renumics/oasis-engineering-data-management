---
title: Lakehouse Formats
description: Open table formats that bring ACID transactions, schema evolution and time-travel to data lakes
type: tool-category
domain: data-storage
tags:
  - lakehouse
  - iceberg
  - delta-lake
  - parquet
  - object-storage
---

# 🧊 Lakehouse Formats

Open table formats that bring ACID transactions, schema evolution and time-travel to data lakes — turning cheap object storage into a full data lakehouse.

| Logo | Name | Description | License |
|------|------|-------------|---------|
| <img src="../logos/iceberg.svg" width="40"/> | [Apache Iceberg](https://iceberg.apache.org/) | Open table format for huge analytic datasets with schema evolution, partition evolution, hidden partitioning and time-travel queries. De-facto standard for modern lakehouses. | Apache 2.0 |
| <img src="../logos/delta-lake.svg" width="40"/> | [Delta Lake](https://delta.io/) | Open storage layer that brings ACID transactions to data lakes. Originally created by Databricks, now widely adopted including in Microsoft Fabric. Supports merge, schema enforcement and time-travel via transaction logs. | Apache 2.0 |
| <img src="../logos/ducklake.svg" width="40"/> | [DuckLake](https://github.com/duckdb/ducklake) | Lightweight lakehouse catalog that stores metadata in a DuckDB (or PostgreSQL/MySQL) database while data lives in Parquet on object storage. Combines simplicity of a database catalog with lakehouse scalability. | MIT |

## See also

- [Query Engines](query-engines.md) — engines that read from lakehouse tables
- [Data Catalogues](data-catalogues.md) — catalogs for managing lakehouse table metadata
- [Time Series Data Tools](time-series-data.md) — extraction tools that produce Parquet for lakehouse ingestion
- [← Back to overview](../README.md)
