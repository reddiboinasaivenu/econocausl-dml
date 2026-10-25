# EconoCausal-DML

*Dynamic Pricing Using Double Machine Learning*

## 📅 Day 1 — Project Setup and Data Preparation Planning

*Role:* Data Collection & Preprocessing Specialist  
*Branch:* data-prep

### Tasks Completed
- Reviewed the EconoCausal project objectives and the data collection and preprocessing requirements.
- Identified the raw JSON data assets: portfolio.json, profile.json, and transcript.json.
- Defined the data organization requirements under Data/Raw/.
- Established the data dictionary requirements for customer profiles, campaign portfolios, and transaction event logs.
- Reviewed the project development roadmap and the subsequent data preparation requirements.

### Documentation and Repository Work
- Initialized the project repository and prepared the main README documentation.
- Created the data dictionary at Data/data_dictionary.md, documenting the relevant data categories and fields, as reported in the project status document.

### Current Status
- Data schema documentation is prepared according to the project status report.
- The data preparation workflow is ready for the next stage of tabular merging and cleaning.

### Next Steps
- Verify and organize the raw JSON datasets.
- Validate field names, data types, missing values, and data consistency.
- Develop scripts to merge and clean the datasets.
- Prepare the processed data for subsequent causal inference and Double Machine Learning workflows.


## 📅 Day 2 — Data Preprocessing and Repository Synchronization

*Role:* Data Collection & Preprocessing Specialist  
*Branch:* `data-prep`  
*Phase:* Data Preparation & Setup  
*Status:* ✅ Completed & Synced

### Tasks Completed

- Processed the raw observational JSON datasets: `profile.json`, `portfolio.json`, and `transcript.json`.
- Developed a repeatable data preprocessing pipeline to clean and transform raw JSON data into structured CSV files.
- Handled complex data types, including dictionaries and lists, to resolve unhashable type errors during deduplication.
- Standardized corrupted age values by converting the invalid age `118` to `NaN`.
- Parsed membership dates into the standard ISO date format.
- Serialized nested channel lists to support safe deduplication.
- Unnested value dictionaries and normalized interaction event logs.
- Verified the cleaned datasets for downstream data analysis and causal modeling.

### Technical Implementation

- **Preprocessing Script:** Developed `src/data_preprocessing.py` to automate the data cleaning workflow.
- **Complex Data Handling:** Implemented `stringify_complex_cols()` using Python's `json.dumps()` to make complex column values hashable for deduplication.
- **Data Cleaning:** Handled invalid demographic values, standardized membership dates, and transformed nested JSON structures into suitable tabular formats.
- **Data Organization:** Saved the processed datasets in the `Data/Processed/` directory.

### Processed Datasets

| File Name | Key Processing Actions |
|---|---|
| `cleaned_profile.csv` | Standardized invalid age values and parsed membership dates into ISO format. |
| `cleaned_portfolio.csv` | Serialized nested channel lists for safe deduplication. |
| `cleaned_transcript.csv` | Unnested value dictionaries and normalized interaction event logs. |

**Dataset Status:** All three processed datasets were verified according to the Day 2 preprocessing report.

### Documentation and Repository Work

- Updated `README.md` with data preprocessing instructions, processed dataset locations, and development roadmap progress.
- Marked Week 1 as completed in the development roadmap.
- Staged and committed the local changes.
- Pushed the updated code, documentation, and processed-data changes to the remote repository.
- Synchronized the `data-prep` branch with the remote Git repository.

### Key Achievements

- Successfully completed the initial data engineering and preprocessing milestone.
- Resolved complex data type issues during deduplication.
- Converted raw observational JSON data into cleaned, structured CSV datasets.
- Improved data consistency and prepared the data foundation for causal inference.
- Completed documentation and synchronized repository changes with the remote branch.

### Current Status

The data collection and preprocessing phase has been completed successfully. The cleaned datasets are available under `Data/Processed/`, and the repository has been synchronized with the remote `data-prep` branch.

### Next Steps — Phase 2: Causal Modeling

- Perform Exploratory Data Analysis (EDA) on the cleaned datasets.
- Identify relevant treatment, outcome, and confounding variables.
- Explore relationships among customer profiles, campaign portfolios, and interaction events.
- Initialize Directed Acyclic Graphs (DAGs) using DoWhy to represent causal relationships.
- Prepare the data and modeling workflow for uplift estimation using EconML and Double Machine Learning (DML).


# EconoCausal – Day 3 Work Report

## Project Title
**EconoCausal: Dynamic Pricing via Double Machine Learning (DML)**

## Work Area
Dataset Collection and Data Preprocessing

## Objective
To identify a suitable retail dataset and prepare it for subsequent project analysis through systematic data cleaning and preprocessing.

## Work Completed

### 1. Dataset Suitability Review
- Reviewed the existing Starbucks dataset to determine its suitability for the dynamic-pricing project.
- Selected the **Online Retail II dataset** because it contains transaction dates, product identifiers, and product descriptions.

### 2. Dataset Collection and Organization
- Obtained the Online Retail II Excel dataset.
- Organized the raw dataset in the project's `Data/Raw` directory.
- Communicated the dataset selection and progress updates with the project team.

### 3. Data Preprocessing
- Updated the preprocessing script to verify that the raw Excel dataset exists before loading it.
- Loaded both worksheets from the Online Retail II dataset:
  - Year 2009–2010: 525,461 rows
  - Year 2010–2011: 541,910 rows
- Combined the worksheets into a single dataset.
- Standardized column names.
- Removed duplicate records.
- Converted date and numerical columns to appropriate data types.
- Created additional derived fields:
  - `is_return`: Identifies transactions with negative quantities.
  - `customer_id_missing`: Indicates missing customer IDs.
  - `transaction_value`: Represents the transaction value.

### 4. Output Generation
Generated the cleaned dataset locally at:

`Data/Processed/online_retail_cleaned.csv`

**Output dataset details:**
- Rows: 1,055,238
- Columns: 12
- Format: CSV

### 5. Version Control
- Updated the preprocessing workflow with raw-file validation.
- Committed and pushed the preprocessing validation update to the `data-prep` branch.
- Generated the cleaned dataset locally for subsequent analysis.

## Deliverables
- Selected and organized the Online Retail II raw dataset.
- Updated the preprocessing workflow with raw-file validation.
- Generated the cleaned dataset containing 1,055,238 rows and 12 columns.
- Pushed the preprocessing validation code update to the `data-prep` branch.

## Project Status
Dataset collection and preprocessing activities were completed for this work period. The Online Retail II dataset was consolidated, cleaned, and saved as a processed CSV file for future project analysis.

## Conclusion
During 19–20 October 2026, the work focused on dataset collection and preprocessing for the EconoCausal project. The Online Retail II dataset was selected, consolidated, cleaned, and saved as a local processed file. The preprocessing validation update was also committed and pushed to the project's `data-prep` branch.

---
**Project:** EconoCausal – Dynamic Pricing via Double Machine Learning (DML)  
**Work Period:** 19–20 October 2026  
**Branch:** `data-prep`
