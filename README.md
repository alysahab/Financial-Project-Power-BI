# Financial-Project-Power-BI
# Automated Financial Data Analysis Pipeline

## Overview

This repository contains a zero-touch pipeline that automates the ingestion, processing, and visualization of daily financial survey data received via email. By leveraging Microsoft Power Automate, Outlook Rules, Python, cloud storage APIs, Power Query, and Power BI, the system retrieves attachments, consolidates and cleans data, and publishes an interactive dashboard—all without manual intervention.

## Problem Statement

Every day by 3 pm, our team receives \~25 CSV and Excel files from a geographically distributed US government survey team. We needed to deliver a consolidated dashboard by 8 pm. Manual handling was time-consuming, error-prone, and costly (\$12K/month in labor). The automation pipeline solves these challenges by:

* **Eliminating manual steps** (zero-touch)
* **Ensuring data accuracy** through programmatic cleaning
* **Reducing costs** by automating repetitive tasks
* **Scaling** to handle growing data volumes and requirements

## Architecture & Workflow

1. **Email Collection**: Outlook Rule filters incoming survey emails containing the keyword `credit score` into a dedicated folder.
2. **Attachment Extraction**: Power Automate Cloud Flow (using Microsoft Graph API) downloads attachments to a Google Drive folder.
3. **File Consolidation**: Python script (Google Drive API v3 + `pandas`) lists, downloads, and merges files into a single DataFrame.
4. **Transformation**: Power Query M-code in Power BI performs type conversions, deduplication, null filtering, and computes derived columns (AgeGroup, LTV).
5. **Visualization**: Power BI dashboard with DAX measures and custom visuals (distribution plots, cohort charts) published to Power BI Service for daily refresh.

## Key Features

* **Automated Ingestion**: Files move from email to cloud storage without manual download.
* **ETL Script**: Python-powered merge of heterogeneous file formats.
* **Data Cleaning**: Power Query transformations with performance optimizations.
* **Dynamic Dashboard**: Interactive filters, slicers, and visual insights updated daily.
* **LTV & Promotions**: Cohort-based LTV calculation and promotion rules integrated.

## Getting Started

### Prerequisites

* Microsoft 365 account with Outlook and Power Automate access
* Google Service Account with Drive API access
* Python 3.7+
* Power BI Desktop
