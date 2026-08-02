
<p align="center">
  <img src="OASIS-EDM-hero.png" alt="OASIS-EDM Hero" width="100%"/>
</p>


# ⚠️ Challenges in engineering data management

Engineering Data Management (EDM) means to capture, store, version, analyze and distribute all data that arise during the lifecycle of a product. For complex electro-mechanical products EDM is a very hard problem spanning many disciplines and systems: CAD models of the product might be stored in the PLM system, simulation data in SDM/SPDM, test in data in the test data management system, the BOM in the ERP system, production data in MES and operational data in an IOT database. And this list is just a tiny fraction of the real world complexity (automotive OEMs have hundreds of different systems). 

We talked a lot about the digital thread and digital twins over the last decade. Unfortunately, even the best engineering teams still do not have a holistic view on their product. Here is a list of some straight forward tasks most organizations struggle with:

- Compare test and simulation data over different product iterations 
- Use information on product usage to enable data-driven product management
- Take design decisions on manufacturability from real production data


# 🤖 A new AI native stack for engineering data management

Agentic AI promises to break the data silos and finally empower engineers to see things end-to-end again. However, results with AI assistants have been mixed so far: Give an AI assistant a folder with documents and tables and ask a complex questions and the results are nearly magical. But using agentic AI systems on top of legacy data infrastructure quickly falls of a cliff (if it is possible at all).

It is time to re-build the engineering data stack with AI-native primitives. This repo presents a new approach to EDM built on the open knowledge format (OKF) (link here). Markdown with structured frontmatter is used to describe concepts that can link to each other. Concepts can reference exernal resources (e.g. tables for structured data or native files for images, geometry) where necessary. The resulting data structure is (an) OASIS:

- **Open**: Not only are all formats completely open, but there proven open-source tools exist for storing, querying and editing the data.
- **AI-native**: By putting OKF bundles in a database, AI agents can efficiently search for information through the resulting knowledge graph, content embeddings and structured frontmatter information.
- **Simple**: Because OKF is just markdown with a few conventions, you can build your first knowledge bundle in less than an hour.
- **Interopable**: Because the data structures can ingest, enrich or just link to resources in existing systems, it can work alongside existing EDM infrastructure.
- **Scalable**: Not only can OKF link to tables that contain PBs of data, but OKFs can also link together to a company-wide knowledge graph.


This repos serves as an introduction and curated lists regarding tooling, datasets and best practices for ‚OKF-based engineering data management.


# 🙌 Why should you care and how can you contribute?

It is only day 1 for building AI in engineering. If you feel the pain of broken engineering data infrastructure yourself or are passionated about giving agency back to engineers, then please help. 

Here are some things you could do:
- Test the system in your workflows starting with a simple folder with markdowns and available tooling.
- If you have some ideas/thoughts/doubts that you want to share, please open a discussion or connect with me for a coffee talk.
- The best way for the community to get a feel for the approach are examples. If you have a dataset that is relevant for the community, please create a PR so we can list it in this repo.
- Please create a PR if you feel an important tool is missing from the list.


# ⚙️ How it works


## 📄 Open Knowledge Format (OKF)

The foundational primitive of the concept are markdown files that are stored in a folder structure. Each markdown file also carries a YAML-block with structured metadata information which is called [frontmatter](https://jekyllrb.com/docs/front-matter/). These text-based folder structures can be versioned an managed in existing systems such as [GIT](https://git-scm.com/).

This basic structure was popularized as [LLM-Wiki](https://github.com/lucasjinreal/llm-wiki) and formalized into a minimal spec by Google under the term [Open Knowledge Format](https://github.com/google/open-knowledge-format). We won't repeat the full spec here, but only highlight the most important aspects:

1. Each markdown contains exactly one Concept
2. Concepts can link together to other concepts creating a knowledge graph
3. External data files (e.g. tables, images) can be linked to as resources

## 📊 Data lakehouse for tabular and time series data

Tabular and time series data is probably the most critical data type in engineering. Engineering teams have already started to move test-, simulation-, production data from legacy formats or databases into general purpose [Parquet](https://parquet.apache.org/) and [lakehouse](https://www.databricks.com/glossary/data-lakehouse)-based systems. Lakehouse systems overcome traditional data silos while providing cheap storage, traceability and scalability.

Both Parquet sources on file/blob/S3 storage and real lakehouse endpoints such as [Delta Lake](https://delta.io/) or [Iceberg](https://iceberg.apache.org/) can be directly referenced from the OKF markdown files as resources. 

The markdown file itself the describes the concept for each table and additional semantic information on how to use it (e.g. example queries, domain-specific information, data models as [Mermaid](https://mermaid.js.org/) diagram). It thus enhances the existing data catalogue information and provides a lightweight semantic layer.

## 📎 References to native formats (image, CAD, CAE etc.)

There are dozens of important data formats in engineering and a lot of effort has been spent to standardize many times of data (e.g. ASAM MDF, STEP 242 (correct?), JT (insert iso here)). Every existing engineering authoring tool and many analysis pipelines depend on this infrastructure. The new OKF-based EDM layer is not supposed to replace it.

Instead, existing files and repositories can simply be referenced in the markdown files. This gives an immediate benefit: The resources are indexed and can easily be found by AI-native search through similarity search or knowledge graph traversal. The OKF-description thus act as an additional analytics layer to the native operational data.

It also makes sense to extract data from source documents and enrich it to facilitate better downstream analysis. Here are some examples for typical extraction and enrichment:
- Dimensions, material properties and parametrizations of a CAD geometry
- Textual description of an image content
- Comparison of two CAE models in terms of parameters and KPIs


# 🔧 Tooling for data extraction and enrichment

## 📈 Time series data

| Logo | Name | Description | License |
|------|------|-------------|---------|
| <img src="logos/asammdf.png" width="40"/> | [asammdf](https://github.com/danielhrisca/asammdf) | Parses automotive MDF data into DataFrames and Parquet files | LGPL-3.0 |
| <img src="logos/generic-tool.svg" width="40"/> | [cantools](https://github.com/cantools/cantools) | Decodes and encodes CAN/LIN/J1939 bus signals from DBC, KCD and ARXML databases | MIT |
| <img src="logos/generic-tool.svg" width="40"/> | [npTDMS](https://github.com/adamreeve/npTDMS) | NumPy-based Python module for reading TDMS files produced by LabVIEW, Diadem and other NI products | LGPL-3.0 |

## 🏎️ CAX data

| Logo | Name | Description | License |
|------|------|-------------|---------|
| <img src="logos/lasso.png" width="40"/> | [Lasso](https://github.com/open-lasso-python/lasso-python) | Toolkit for processing CAE (crash, NVH) simulation results including D3plot, Binout and FEMZIP | BSD-3-Clause |
| <img src="logos/opencascade.png" width="40"/> | [OpenCASCADE](https://dev.opencascade.org/) | Open-source CAD/CAM/CAE kernel for 3D modeling, STEP/IGES import/export and geometric computation | LGPL-2.1 |

# 🗄️ Tooling for data storage and analysis

In this section, we exemplary list the most important tools for each category. Please consult an AI assistant of your choice to get a more extensive overview over the ecosystem.

## 🧊 Lakehouses

Open table formats that bring ACID transactions, schema evolution and time-travel to data lakes — turning cheap object storage into a full data lakehouse.

| Logo | Name | Description | License |
|------|------|-------------|---------|
| <img src="logos/iceberg.svg" width="40"/> | [Apache Iceberg](https://iceberg.apache.org/) | Open table format for huge analytic datasets with schema evolution, partition evolution, hidden partitioning and time-travel queries. De-facto standard for modern lakehouses. | Apache 2.0 |
| <img src="logos/delta-lake.svg" width="40"/> | [Delta Lake](https://delta.io/) | Open storage layer that brings ACID transactions to data lakes. Originally created by Databricks, now widely adopted including in Microsoft Fabric. Supports merge, schema enforcement and time-travel via transaction logs. | Apache 2.0 |
| <img src="logos/ducklake.svg" width="40"/> | [DuckLake](https://github.com/duckdb/ducklake) | Lightweight lakehouse catalog that stores metadata in a DuckDB (or PostgreSQL/MySQL) database while data lives in Parquet on object storage. Combines simplicity of a database catalog with lakehouse scalability. | MIT |

## 🔍 Query engines

Analytical query engines that can read directly from lakehouse tables and Parquet files — enabling fast interactive analytics on engineering data without ETL.

| Logo | Name | Description | License |
|------|------|-------------|---------|
| <img src="logos/spark.png" width="40"/> | [Apache Spark](https://spark.apache.org/) | Unified engine for large-scale batch and streaming data processing. Industry standard for ETL pipelines and distributed analytics on lakehouse data. | Apache 2.0 |
| <img src="logos/duckdb.png" width="40"/> | [DuckDB](https://duckdb.org/) | In-process OLAP database with zero external dependencies. Reads Parquet, CSV, JSON and Iceberg/Delta directly. Ideal for local engineering data exploration. | MIT |
| <img src="logos/starrocks.svg" width="40"/> | [StarRocks](https://www.starrocks.io/) | High-performance MPP analytical database for real-time and batch analytics. Supports external catalogs for Iceberg and Delta Lake federation. | Apache 2.0 |
| <img src="logos/bigquery.png" width="40"/> | [BigQuery](https://cloud.google.com/bigquery) | Google's fully managed, serverless data warehouse with built-in ML and BI. Supports Iceberg tables and external data lake connections. | Proprietary |
| <img src="logos/athena.png" width="40"/> | [Amazon Athena](https://aws.amazon.com/athena/) | Serverless query service that analyzes data in S3 using SQL. Native support for Parquet, Iceberg and other open formats with pay-per-query pricing. | Proprietary |

## 📚 Data catalogues

| Logo | Name | Description | License |
|------|------|-------------|---------|
| <img src="logos/unity-catalog.png" width="40"/> | [Unity Catalog](https://www.unitycatalog.io/) | Open-source universal catalog for data and AI assets. Provides governance, access control and lineage across lakehouses and ML models. | Apache 2.0 |
| <img src="logos/polaris.svg" width="48"/> | [Apache Polaris](https://polaris.apache.org/) | Open-source catalog for Apache Iceberg. Provides a REST-based catalog interface with multi-engine access, role-based access control and credential vending. | Apache 2.0 |
| <img src="logos/nessie.svg" width="40"/> | [Project Nessie](https://projectnessie.org/) | Git-like version control for data lakes. Provides branching, tagging and commits for Iceberg tables enabling isolated experimentation and reproducibility. | Apache 2.0 |

## 🏷️ Metadata management & data lineage

Tools for cataloging datasets, tracking lineage and providing a semantic layer on top of raw engineering data.

| Logo | Name | Description | License |
|------|------|-------------|---------|
| <img src="logos/datahub.svg" width="40"/> | [DataHub](https://datahubproject.io/) | Extensible metadata platform for data discovery, observability, and governance. Supports automated lineage and integrations with most lakehouse engines. | Apache 2.0 |
| <img src="logos/openmetadata.png" width="40"/> | [OpenMetadata](https://open-metadata.org/) | End-to-end metadata management platform with data discovery, lineage, quality, profiling and collaboration. Supports connectors for 50+ data services. | Apache 2.0 |
| <img src="logos/collibra.png" width="40"/> | [Collibra](https://www.collibra.com/) | Enterprise data intelligence platform providing data cataloging, governance, lineage and quality management at scale. Industry leader for regulated environments. | Proprietary |
| <img src="logos/atlan.png" width="40"/> | [Atlan](https://atlan.com/) | Active metadata platform with embedded collaboration, automated lineage and AI-powered search. Designed for modern data teams with a developer-first approach. | Proprietary |

# 📦 Example datasets

## 📏 Testing data

## 🚗 Fleet data

## 🏭 Production data

- **[Industrial Asset Level Electrical Energy Dataset](https://huggingface.co/datasets/renumics/industrial-asset-level-electrical-energy-dataset)** provides 15-minute energy aggregates from an industrial manufacturing facility in Ireland. The source dataset covers 43 monitored assets over ~12 months (2024-12-31 to 2025-12-31).

## 💻 Simulation data

# ❓ Frequently asked questions

## What is an engineering data analytics layer?

For business intelligence and general data analytics applications, data is not directly pulled from the transactional systems. Instead, the data is ingested into so-called online analytical processing (OLAP) databases that operate on columnar storage with heavy compression for efficient queries. An engineering data analytics layer brings this concept to EDM: A system that brings together operational data from different sources for analytical/reporting applications. 


## Do you really want to replace the existing ERP/PLM infrastructure with this?

Short answer: No. Longer answer: The current generation of enterprise data management systems are intertwined with every single enterprise process and impossible to replace. However, OASIS-EDM can work as an analytics layer on top of the legacy operational engineering data layer. In this way, OASIS enables a holistic view on engineering data without compromising existing systems. From there it is absolutely possible to shift more and more processes to OKF-compatible tools: Requirements management, bug tracking, reporting etc.


## My management loves PowerPoint too much, they will never accept markdown reports

There is a big difference between generally describing insights and facts for future use and presenting such content in a limited amount of time for a specific audience (e.g. speech, status meeting). PowerPoint is a great tool for the latter, but is heavily misused for the former.
Example: For a scientific conference you would hand in a paper written in LateX (general description of content) and then might do your presentation slides in PP. 
With agents, this paradigm will get even more important. You should describe all the facts and insights in markdown. Then you can push a button and get a tailored presentation (or even a video) for your stakeholders. So: You can still do PowerPoint reports, but only as a presentation output and not as a source of truth for facts and insights!






