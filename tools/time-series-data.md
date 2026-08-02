---
title: Time Series Data Tools
description: Tools for extracting and converting engineering time series data (MDF, TDMS, CAN) into analysis-ready formats like Parquet
type: tool-category
domain: data-extraction
tags:
  - time-series
  - mdf
  - tdms
  - can-bus
  - parquet
---

# 📈 Time Series Data Tools

Tools for extracting engineering time series data from proprietary formats and converting them into open, analysis-ready formats like Parquet and DataFrames.

| Logo | Name | Description | License |
|------|------|-------------|---------|
| <img src="../logos/asammdf.png" width="40"/> | [asammdf](https://github.com/danielhrisca/asammdf) | Parses automotive MDF data into DataFrames and Parquet files | LGPL-3.0 |
| <img src="../logos/generic-tool.svg" width="40"/> | [cantools](https://github.com/cantools/cantools) | Decodes and encodes CAN/LIN/J1939 bus signals from DBC, KCD and ARXML databases | MIT |
| <img src="../logos/generic-tool.svg" width="40"/> | [npTDMS](https://github.com/adamreeve/npTDMS) | NumPy-based Python module for reading TDMS files produced by LabVIEW, Diadem and other NI products | LGPL-3.0 |

## See also

- [Lakehouse Formats](lakehouses.md) — store extracted time series data in open table formats
- [Query Engines](query-engines.md) — analyze extracted time series data with SQL
- [← Back to overview](../README.md)
