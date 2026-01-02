# Processed Data Layer

This directory represents the logical processed layer of the data pipeline.

In this project, all data transformations, cleansing, and enrichment steps are performed inside Power BI using Power Query.  
As a result, no materialized processed data files (e.g. CSV or Parquet) are stored in this repository.

The directory is intentionally kept to reflect the layered ETL design:
raw → staging → final (semantic model).
