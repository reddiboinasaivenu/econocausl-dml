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



## 📅 Day 4 — Data Preprocessing and DML Dataset Preparation

**Date:** October 22, 2026  
**Phase:** Data Collection & Preprocessing  
**Role:** Data Collection & Preprocessing Specialist  
**Branch:** `data-prep`  
**Target PR:** `main`  
**Status:** Completed

### 🎯 Objective

Complete the end-to-end data processing pipeline for the EconoCausal project by cleaning the Starbucks datasets and preparing the UK Online Retail II (2009–2011) dataset for Double Machine Learning (DML) estimation.

### ✅ Tasks Completed

#### 1. Starbucks Dataset Cleaning
- Standardized and deduplicated `portfolio.json`, `profile.json`, and `transcript.json`.
- Converted complex nested data types into string representations to support reliable deduplication.
- Cleaned missing demographic information.

#### 2. Online Retail II Dataset Consolidation
- Merged the two yearly datasets into one unified dataset.
- Consolidated the 2009–2010 dataset containing 525,461 rows and the 2010–2011 dataset containing 541,910 rows.
- Prepared the consolidated data for further preprocessing and modeling.

#### 3. DML Data Filtering and Cleaning
Applied the following filtering rules to prepare the modeling dataset:

- Removed return and cancellation records where the invoice number starts with `C`.
- Removed records with `Quantity <= 0`.
- Retained records with positive unit prices (`unit_price > 0`).
- Removed records with missing `customer_id`.
- Replaced missing product descriptions with `UNKNOWN`.
- Removed exact duplicate rows across all fields.

#### 4. Git LFS Configuration
- Configured Git Large File Storage (LFS) to track large dataset files.
- Added Git LFS tracking for `cleaned_online_retail_dml.csv`.
- Prepared the approximately 83.9 MB CSV dataset for GitHub upload without standard Git file-size warnings.

### 📂 Deliverables

| File Path | Type | Description |
|---|---|---|
| `src/data_preprocessing.py` | Python script | Automated data cleaning pipeline and DML dataset exporter |
| `Data/Processed/cleaned_online_retail_dml.csv` | CSV (approximately 83.9 MB) | Final DML modeling-ready dataset |
| `.gitattributes` | Git LFS configuration | Tracks large CSV outputs using Git LFS |

### 📊 Results

- Successfully generated **793,609 clean records** for DML modeling.
- Standardized and deduplicated the Starbucks datasets.
- Consolidated the UK Online Retail II datasets into a unified dataset.
- Applied filtering rules to remove invalid transactions and missing customer identifiers.
- Configured Git LFS for handling the large processed CSV file.

### 📁 Final Dataset Location

```text
Data/
└── Processed/
    └── cleaned_online_retail_dml.csv
```

### 🚀 Outcome

Completed the data preprocessing pipeline and generated a clean, modeling-ready dataset for the EconoCausal Double Machine Learning project. The processed dataset and supporting preprocessing script are organized in the repository, with Git LFS configured for large-file tracking.

**Day 4 Status: Completed ✅**


## 📅 Day 5 — Double Machine Learning (DML) Implementation and Initial Results

**Project:** EconoCausal — Dynamic Pricing via Double Machine Learning  
**Role:** Data Collection & Preprocessing Specialist  
**Branch:** `data-prep`  
**Treatment Variable:** `unit_price`  
**Outcome Variable:** `quantity`

### 🎯 Objective

The objective was to implement an initial Double Machine Learning (DML) pipeline to estimate the effect of product price on purchase quantity. The work focused on preparing the modeling dataset, fitting machine-learning nuisance models, estimating individual treatment effects, and performing initial uplift and robustness analyses.

### ✅ Tasks Completed

- Prepared the modeling dataset using the cleaned Online Retail II transaction data.
- Identified `unit_price` as the treatment variable and `quantity` as the outcome variable.
- Selected product, geographic, and temporal covariates based on the preliminary causal Directed Acyclic Graph (DAG).
- Implemented the `LinearDML` estimator from EconML.
- Split the data into training and testing sets for model development and evaluation.
- Trained nuisance models to predict the outcome (`quantity`) and treatment (`unit_price`) using the selected covariates.
- Applied cross-fitting to reduce overfitting bias during nuisance estimation.
- Generated Individual Treatment Effects (ITEs) for the test population.
- Conducted an initial Qini uplift analysis to explore differences in estimated treatment effects.
- Used DoWhy refutation checks, including placebo treatment, random common cause, and data-subset refuters, to examine the robustness of the initial estimates.

### 📊 Initial Results

- **Model:** EconML `LinearDML`
- **Dataset:** UK Online Retail II (2009–2011)
- **Modeling records:** 793,609
- **Treatment:** `unit_price`
- **Outcome:** `quantity`
- **Mean estimated treatment effect:** Approximately `-0.86` quantity units per one-unit increase in price.

The initial results indicate a negative relationship between product price and purchase quantity after adjusting for the selected covariates. The estimated mean effect is preliminary and depends on the current dataset, model specification, and causal identification assumptions.

### 🛠️ Technologies Used

- Python
- Pandas and NumPy
- Scikit-learn
- EconML
- DoWhy
- Git and Git LFS

### 🔍 Analysis and Inferences

The initial DML pipeline successfully generated Individual Treatment Effects, providing a foundation for analyzing how price sensitivity may vary across observations.

The Qini uplift analysis was exploratory and requires further validation before it can support pricing decisions. The DoWhy refutation tests provide useful diagnostic checks but do not prove that all causal assumptions hold.

The results suggest that higher prices may reduce purchase quantities under the current model specification. However, further analysis is required to evaluate uncertainty, overlap, unobserved confounding, and model sensitivity.

### ⚠️ Limitations

- The estimated effect has not yet been supported by confidence intervals or other uncertainty measures.
- Unobserved factors, such as competitor prices, promotions, and stock availability, may influence the estimates.
- Price overlap across product and time groups needs to be examined.
- The Qini uplift analysis requires additional validation.
- The findings should not be used for operational pricing decisions until the required robustness and validation checks are completed.

### 🚀 Next Steps

- Calculate confidence intervals for the mean treatment effect and individual effects where appropriate.
- Perform data-quality checks for missing values, duplicates, outliers, and variable units.
- Examine price overlap and positivity across product and time groups.
- Conduct sensitivity analysis for unobserved confounding.
- Compare alternative model specifications and baseline regression models.
- Validate uplift performance.
- Begin planning the SciPy budget-allocation solver and React experimentation dashboard.

### 📁 Key Project Files

| File | Purpose |
|---|---|
| `src/data_preprocessing.py` | Data cleaning and modeling dataset generation |
| `Data/Processed/cleaned_online_retail_dml.csv` | Final DML modeling dataset |
| `Data/data_dictionary.md` | Data dictionary documentation |
| `README.md` | Project overview and execution instructions |
| `.gitattributes` | Git LFS configuration |

### 📝 Conclusion

The initial Double Machine Learning implementation established a foundation for estimating the causal effect of product prices on purchase quantities. The pipeline generated individual treatment effects and a preliminary mean effect of approximately -0.86 quantity units per one-unit increase in price. Further statistical validation, sensitivity analysis, and uplift evaluation are required before using these findings for business pricing decisions.

## 📅 Day 6 — API & Packaging and Dashboard Refinement

**Project:** EconoCausal – Dynamic Pricing Using Double Machine Learning  
**Role:** Data Collection & Preprocessing Specialist  
**Branch:** `data-prep`

### 🎯 Objectives

- Wrap the causal inference engine into a REST API.
- Prepare the model for integration with the application.
- Develop an automated data drift detection mechanism.
- Improve the dashboard user experience.
- Add natural language summaries to explain business results.

### 1. API Development and Packaging

- Planned to expose the EconoCausal causal engine through a REST API using FastAPI.
- Designed the API workflow to accept customer and transaction data and return causal effect estimates.
- Planned API endpoints for model predictions, treatment effect estimation, and model health monitoring.
- Prepared the integration approach for connecting the Python-based causal engine with the React dashboard.
- Focused on making the model accessible, reusable, and easier to deploy.

### 2. Automated Data Drift Detection

- Planned an automated data drift detection mechanism to monitor changes in incoming customer and transaction data.
- Identified important variables such as `unit_price`, `quantity`, product information, and transaction dates for monitoring.
- Planned to compare incoming data distributions with the reference training dataset.
- Designed the system to generate warnings when significant changes in customer purchasing behavior or data distributions are detected.
- This monitoring process will help identify when the causal model may require validation or retraining.

### 3. Dashboard Refinement and Improvements

- Planned improvements to the React-based dashboard to make analytical results easier to understand.
- Focused on presenting causal estimates, customer responsiveness, and business performance metrics clearly.
- Planned to improve the visualization of Qini uplift curves and targeting efficiency.
- Worked toward creating a simple and user-friendly interface for business stakeholders.

### 4. Natural Language Business Summaries

- Planned to introduce automatically generated natural language summaries.
- The summaries will explain model results in simple business language.
- Designed example messages such as:

  - "This strategy saves $4,200 compared to blanket targeting."
  - "Targeted pricing provides better efficiency than applying the same strategy to all customers."
  - "The model identifies customers with different levels of price responsiveness."

- Planned to calculate savings and performance comparisons using actual model outputs rather than fixed values.

### 5. Expected Benefits

- Improved accessibility of the causal inference engine through REST APIs.
- Easier integration between the backend model and frontend dashboard.
- Early warnings when incoming customer behavior changes.
- Better monitoring of model reliability.
- Improved understanding of causal analysis through simple business summaries.
- Better support for data-driven pricing and customer-targeting decisions.

### 6. Current Status

| Component | Status |
|---|---|
| Causal engine | Initial implementation available |
| FastAPI REST API | Planned / In Progress |
| API packaging | Planned |
| Data drift detector | Planned |
| React dashboard integration | Planned |
| Natural language summaries | Planned |
| Deployment and testing | Pending |

### 7. Next Steps

- Implement and test FastAPI endpoints.
- Connect the API with the existing causal inference engine.
- Develop statistical data drift monitoring.
- Integrate drift warnings into the dashboard.
- Implement dynamic business summaries using actual model results.
- Perform end-to-end API and dashboard testing.

### Conclusion

Day 6 focuses on moving the EconoCausal project toward a deployable and user-friendly causal AI application. The main objectives are to expose the causal engine through REST APIs, monitor changes in customer behavior using automated data drift detection, and improve the React dashboard with meaningful visualizations and natural language business summaries. These improvements will help transform causal analysis results into understandable and actionable business insights.

