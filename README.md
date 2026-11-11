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


## 📅 Day 7 — Dashboard Refinement and Natural Language Summaries

### Objective
Refine and polish the EconoCausal dashboard by improving its user interface and introducing simple natural-language summaries that help users understand causal analysis results and business outcomes.

### Tasks Completed
- Refined the dashboard layout to improve usability and visual presentation.
- Improved the organization of dashboard components, charts, and performance metrics.
- Focused on presenting causal analysis results in an understandable format.
- Planned natural-language summaries to explain the business impact of different targeting strategies.
- Worked on making complex analytical results easier for non-technical stakeholders to understand.
- Focused on comparing optimized targeting strategies against blanket targeting approaches.

### Natural Language Business Summaries 
The dashboard is designed to display simple business-oriented explanations, such as:

- "This strategy saves $4,200 compared to blanket targeting."
- "Optimized targeting helps reduce unnecessary campaign spending


## 📅 Day 7 — Dashboard Refinement and Natural Language Summaries

### Objective
Refine and polish the EconoCausal dashboard by improving its user interface and introducing simple natural-language summaries that help users understand causal analysis results and business outcomes.

### Tasks Completed
- Refined the dashboard layout to improve usability and visual presentation.
- Improved the organization of dashboard components, charts, and performance metrics.
- Focused on presenting causal analysis results in an understandable format.
- Planned natural-language summaries to explain the business impact of different targeting strategies.
- Worked on making complex analytical results easier for non-technical stakeholders to understand.
- Focused on comparing optimized targeting strategies against blanket targeting approaches.

### Natural Language Business Summaries 
The dashboard is designed to display simple business-oriented explanations, such as:

- "This strategy saves $4,200 compared to blanket targeting."
- "Optimized targeting helps reduce unnecessary campaign spending



## 📅 Day 7 — Dashboard Refinement and Natural Language Summaries

### Objective
Refine and polish the EconoCausal dashboard by improving its user interface and introducing simple natural-language summaries that help users understand causal analysis results and business outcomes.

### Tasks Completed
- Refined the dashboard layout to improve usability and visual presentation.
- Improved the organization of dashboard components, charts, and performance metrics.
- Focused on presenting causal analysis results in an understandable format.
- Planned natural-language summaries to explain the business impact of different targeting strategies.
- Worked on making complex analytical results easier for non-technical stakeholders to understand.
- Focused on comparing optimized targeting strategies against blanket targeting approaches.

### Natural Language Business Summaries 
The dashboard is designed to display simple business-oriented explanations, such as:

- "This strategy saves $4,200 compared to blanket targeting."
- "Optimized targeting helps reduce unnecessary campaign spending


## 📅 Day 7 — Dashboard Refinement and Natural Language Summaries

### Objective
Refine and polish the EconoCausal dashboard by improving its user interface and introducing simple natural-language summaries that help users understand causal analysis results and business outcomes.

### Tasks Completed
- Refined the dashboard layout to improve usability and visual presentation.
- Improved the organization of dashboard components, charts, and performance metrics.
- Focused on presenting causal analysis results in an understandable format.
- Planned natural-language summaries to explain the business impact of different targeting strategies.
- Worked on making complex analytical results easier for non-technical stakeholders to understand.
- Focused on comparing optimized targeting strategies against blanket targeting approaches.

### Natural Language Business Summaries 
The dashboard is designed to display simple business-oriented explanations, such as:

- "This strategy saves $4,200 compared to blanket targeting."
- "Optimized targeting helps reduce unnecessary campaign spending


## 📅 Day 8 — Prescriptive Optimization & Revenue Maximization

### 🎯 Objective

Develop a prescriptive optimization module using **SciPy** to maximize total predicted revenue while satisfying a strict Allocation Matrix. The objective is to convert causal model predictions into actionable pricing and resource-allocation recommendations.

### 1. Prescriptive Optimization Using SciPy

- Implemented an optimization framework using Python's SciPy optimization library.
- Designed an objective function to maximize total predicted revenue.
- Integrated predicted revenue values from the causal estimation pipeline.
- Defined decision variables representing allocation quantities across eligible products or customer segments.
- Applied optimization constraints to ensure that all allocation decisions follow the predefined Allocation Matrix.
- Used constrained optimization to identify the best feasible allocation strategy.

### 2. Strict Allocation Matrix

Designed an Allocation Matrix to control how available resources are distributed.

Key considerations:

- Enforced predefined allocation limits.
- Prevented allocations to restricted or ineligible segments.
- Ensured that total allocated resources did not exceed the available budget.
- Applied upper and lower bounds to decision variables.
- Validated the optimized allocation against all matrix constraints.

**Purpose:** Ensure that the optimization engine generates feasible, controlled, and business-relevant recommendations rather than unrestricted allocations.

### 3. Revenue Maximization

The optimization engine evaluates possible allocation combinations and selects the configuration that produces the highest predicted total revenue.

**Optimization Objective:**

Maximize:

`Total Predicted Revenue = Σ (Predicted Revenue × Allocation)`

Subject to:

- Total allocation ≤ Available Budget
- Allocation Matrix restrictions
- Minimum allocation requirements
- Maximum allocation limits
- Non-negative decision variables

### 4. Final Prescription UI — Dashboard Development

Designed the UI view to display the final optimization results in a clear and understandable format.

The Prescription dashboard includes:

- Product or customer segment identification.
- Current allocation values.
- Recommended allocation values.
- Predicted revenue contribution.
- Allocation status.
- Optimization results.

### 5. Final Prescription Table

The dashboard presents the optimization output in a structured table.

| Parameter | Description |
|---|---|
| Product / Segment | Target product or customer group |
| Current Allocation | Existing resource allocation |
| Recommended Allocation | Optimized allocation |
| Predicted Revenue | Expected revenue contribution |
| Allocation Status | Within or outside permitted limits |

The final table helps stakeholders understand exactly where resources should be allocated and how the recommended strategy supports revenue maximization.

### 6. Technology Stack

- **Python:** Optimization logic and backend processing.
- **SciPy:** Constrained numerical optimization.
- **NumPy:** Numerical calculations and allocation matrices.
- **Pandas:** Data processing and optimization result tables.
- **React:** Prescription dashboard interface.
- **Plotly.js:** Interactive revenue and allocation visualizations.

### 7. Expected Deliverables

| Deliverable | Purpose |
|---|---|
| `prescriptive_optimization.py` | SciPy revenue optimization engine |
| Allocation Matrix | Defines strict allocation restrictions |
| Optimized Allocation | Stores recommended allocation values |
| Prescription Table | Displays final recommendations |
| Dashboard UI | Visualizes optimization results |

### 8. Key Achievements

- Developed the structure for a SciPy-based prescriptive optimization engine.
- Defined revenue maximization as the primary optimization objective.
- Incorporated strict Allocation Matrix constraints into the optimization design.
- Connected causal predictions with actionable allocation recommendations.
- Designed a structured Prescription table for the dashboard.
- Improved decision transparency by presenting recommended allocations and predicted revenue contributions.

### 9. Next Steps

- Validate the optimization results against all Allocation Matrix restrictions.
- Compare optimized revenue with the existing allocation strategy.
- Integrate the optimization engine with the causal prediction API.
- Complete the React Prescription dashboard.
- Test the system using different budgets and allocation scenarios.

### 📌 Day 8 Outcome

Day 8 focused on moving EconoCausal from causal prediction toward prescriptive decision-making. The optimization framework uses SciPy to identify revenue-maximizing allocation decisions while respecting strict business constraints. The final Prescription UI is designed to translate optimization outputs into an understandable table of recommended allocations, helping stakeholders make data-driven pricing and resource-allocation decisions.


## 📅 Day 9 — Vision Transformer (ViT) Integration

### 🎯 Objective
Integrate a Vision Transformer (ViT) architecture into the existing model using a self-attention mechanism to improve prediction accuracy by identifying complex relationships and patterns across different light spectrums.

### 🚀 Tasks Completed

- Studied the Vision Transformer (ViT) architecture and its self-attention mechanism.
- Explored how transformer-based models capture relationships between different input features.
- Designed the integration of ViT into the existing machine learning workflow.
- Implemented the concept of patch embedding to convert input data into a suitable representation for transformer processing.
- Incorporated positional embeddings to preserve the positional information of input patches.
- Applied multi-head self-attention to identify complex correlations across different light spectrums.
- Explored feature extraction and representation learning using transformer encoder layers.
- Focused on improving the model's ability to understand spectral patterns and relationships.

### 🧠 Vision Transformer Architecture

The Vision Transformer processes input data through the following stages:

1. **Input Processing:** Prepare and normalize the input spectral data.
2. **Patch Embedding:** Divide the input representation into smaller patches and convert them into embeddings.
3. **Positional Embedding:** Add positional information to maintain the relationships between patches.
4. **Multi-Head Self-Attention:** Identify important relationships and dependencies across different spectral features.
5. **Transformer Encoder:** Process the embedded representations using attention and feed-forward layers.
6. **Feature Extraction:** Generate meaningful feature representations for prediction.
7. **Output Layer:** Pass the extracted features to the prediction layer.

### 🔬 Self-Attention Mechanism

- Helps the model focus on important spectral features.
- Captures long-range dependencies between different light spectrums.
- Identifies complex relationships that traditional feature extraction methods may overlook.
- Combines information from multiple attention heads to generate richer feature representations.
- Supports improved feature learning and prediction performance.


## 📅 Day 10 — API & Packaging and Automated Data Drift Detection

### Objective
The main objective of Day 10 was to integrate the EconoCausal Double Machine Learning (DML) engine into a REST API and develop an automated data drift detection mechanism to identify changes in customer behavior and maintain the reliability of causal predictions.

### Tasks Completed

**1. REST API Development**
- Designed a REST API to expose the EconoCausal causal inference engine.
- Integrated the causal estimation workflow with API endpoints.
- Enabled external applications to send customer and pricing data through API requests.
- Structured API responses to return predicted outcomes and estimated treatment effects.
- Improved communication between the backend causal engine and the frontend dashboard.

**2. Causal Engine Integration**
- Connected the Double Machine Learning pipeline with the API layer.
- Enabled the API to process input data and generate causal effect estimates.
- Organized the prediction workflow for easier integration and deployment.
- Improved the modularity and maintainability of the application.

**3. Automated Data Drift Detection**
- Developed a data drift monitoring approach to identify changes in incoming customer data.
- Compared new customer behavior data against the reference dataset.
- Monitored changes in important features and customer behavior patterns.
- Implemented warning notifications when significant distribution changes were detected.
- Designed the monitoring process to help identify situations where the existing causal model may require reassessment.

**4. API Packaging**
- Organized the causal engine and API components into a structured application.
- Prepared the application for integration with the frontend dashboard.
- Improved code organization and reusability.
- Prepared the system for future deployment and production integration.

### Key Outcomes
- Established a REST API architecture for the causal inference engine.
- Connected the DML workflow with an API-based application structure.
- Designed automated data drift monitoring for changing customer behavior.
- Improved the system's maintainability and integration readiness.
- Established a foundation for reliable and scalable causal pricing recommendations.

### Technologies Used
- Python
- REST API
- Double Machine Learning (DML)
- Pandas
- NumPy
- Scikit-learn
- Data Drift Detection
- JSON
- FastAPI / Flask (depending on the framework implemented)

### Project Status
- [x] REST API architecture and integration
- [x] Causal engine API preparation
- [x] Automated data drift detection approach
- [x] API packaging and organization
- [x] Preparation for deployment and dashboard integration

### Next Steps
- Test API endpoints with different input datasets.
- Validate the accuracy and reliability of drift detection.
- Integrate API responses into the React dashboard.
- Implement appropriate alerts for detected data drift.
- Prepare the complete application for deployment.


# Day 11 – Prescriptive Optimization, API Development & Dashboard Refinement

## 1. Prescriptive Optimization Using SciPy

Implemented a prescriptive optimization approach using **SciPy** to maximize total predicted revenue while maintaining a strict marketing budget constraint.

### Key Activities
- Used customer-level treatment effects from the causal engine.
- Developed an optimization model to assign personalized discounts.
- Maximized total predicted revenue for selected customers.
- Applied budget constraints to prevent overspending.
- Used `scipy.optimize.minimize()` to calculate optimal discount allocations.
- Added lower and upper bounds to control discount amounts.

### Objective Function
The optimization model aims to maximize:

- Total predicted revenue.
- Customer-level revenue uplift.
- Marketing budget utilization efficiency.

The optimization problem is formulated as:

\[
\max_{d_1,\ldots,d_n}\sum_{i=1}^{n}R_i(d_i)
\]

Subject to:

\[
\sum_{i=1}^{n}C_i(d_i)\leq B
\]

Where:
- \(d_i\) = Personalized discount for customer i.
- \(R_i\) = Predicted revenue.
- \(C_i\) = Marketing cost.
- \(B\) = Total marketing budget.

## 2. Allocation Matrix – Customer Prescription

Developed an Allocation Matrix to display the mathematically optimized discount recommendations for individual customers.

### Key Activities
- Generated customer-level discount recommendations.
- Displayed customer IDs and optimal discount amounts.
- Included predicted revenue and expected uplift.
- Identified customers receiving the highest optimization benefits.
- Presented the final prescription in a structured dashboard table.

### Prescription Table

| Customer ID | Optimal Discount | Predicted Revenue | Recommendation |
|---|---:|---:|---|
| C001 | 10% | 250 | High Priority |
| C002 | 5% | 180 | Medium Priority |
| C003 | 15% | 320 | High Priority |
| C004 | 0% | 150 | No Discount |

*Note: These are illustrative values. Actual recommendations must come from the optimization model.*

## 3. REST API Development and Packaging

Wrapped the causal engine in a REST API to make the optimization and prediction functionality accessible to other applications.

### Key Activities
- Used Python and FastAPI to develop REST endpoints.
- Integrated the trained causal inference model.
- Created endpoints for customer-level predictions.
- Enabled personalized discount recommendations through API requests.
- Added input validation and error handling.
- Prepared the application for deployment and integration with the dashboard.

### API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| GET | `/` | Check API status |
| GET | `/health` | Health monitoring |
| POST | `/predict` | Generate causal predictions |
| POST | `/optimize` | Generate optimal discount allocations |
| GET | `/prescriptions` | Retrieve customer prescriptions |
| GET | `/drift` | Check data drift status |

## 4. Automated Data Drift Detection

Implemented a data drift monitoring approach to identify changes in customer behavior and incoming data distributions.

### Key Activities
- Compared reference and current customer datasets.
- Monitored important features such as unit price, quantity, and transaction patterns.
- Identified statistical changes in incoming data.
- Generated warnings when significant distribution changes were detected.
- Supported model reliability through continuous monitoring.

### Drift Detection Workflow

1. Load the reference dataset.
2. Load newly collected customer data.
3. Compare feature distributions.
4. Calculate statistical drift indicators.
5. Generate alerts when drift exceeds the configured threshold.
6. Recommend model evaluation or retraining when necessary.

## 5. Dashboard Refinement and Natural Language Summaries

Improved the dashboard to make optimization results easier to understand for business users.

### Key Activities
- Refined the dashboard layout and user interface.
- Integrated the final customer Allocation Matrix.
- Displayed optimized discounts and predicted revenue.
- Added marketing budget utilization metrics.
- Included optimization performance comparisons.
- Generated simple natural-language business summaries.

### Example Business Insights

- Personalized discounts improve marketing budget allocation.
- The optimization model identifies customers with higher expected revenue uplift.
- The budget constraint prevents excessive marketing expenditure.
- Customers with low expected incremental benefit can receive smaller discounts or no discount.

Example summary:

"This strategy saves $4,200 compared to blanket targeting."

*The $4,200 figure is an illustrative example, not a measured project result. Actual savings should be calculated from the optimized and baseline strategies.*

## 6. Technologies Used

| Technology | Purpose |
|---|---|
| Python | Core implementation |
| SciPy | Prescriptive optimization |
| NumPy | Numerical calculations |
| Pandas | Data processing |
| FastAPI | REST API development |
| Scikit-learn | Machine learning and statistical monitoring |
| EconML | Causal effect estimation |
| DoWhy | Causal inference validation |
| React | Dashboard development |
| Plotly.js | Interactive visualizations |

## 7. Expected Project Outcomes

- Developed a budget-constrained optimization framework.
- Generated personalized customer discount recommendations.
- Created a structured customer prescription table.
- Prepared REST API endpoints for causal predictions and optimization.
- Established automated data drift monitoring.
- Improved dashboard usability through natural-language business insights.
- Connected causal inference with practical business decision-making.

## 8. Conclusion

Day 11 focused on transforming the EconoCausal DML project from causal effect estimation into a practical prescriptive decision-support system.

The SciPy optimization module determines personalized discount allocations under strict budget constraints. The Allocation Matrix presents the final customer-level prescriptions. FastAPI provides access to the causal engine, while automated drift detection monitors changes in customer behavior.

Finally, dashboard refinements and natural-language summaries make the results easier for stakeholders to interpret and use in marketing and pricing decisions.

**Status:** Day 11 – Prescriptive Optimization, API Development, Data Drift Detection, and Dashboard Refinement.


## Day 12 – Project Status & Technical Documentation

### 1. Project Overview
EconoCausal is a Causal AI-based project designed to improve promotional campaign efficiency by identifying the true causal impact of discounts on customer conversions.

Traditional predictive machine learning models estimate correlations rather than actual causal relationships. EconoCausal uses Double Machine Learning (DML) to calculate Individual Treatment Effects (ITE) and optimize promotional spending.

### 2. Project Objectives
- Implement Double Machine Learning (DML) for causal effect estimation.
- Use Directed Acyclic Graphs (DAGs) to identify causal relationships.
- Apply propensity score matching to balance observational campaign data.
- Optimize personalized discount allocation under strict budget constraints.
- Develop an interactive dashboard to visualize uplift and campaign efficiency.

### 3. Core Modules and Technologies

| Module | Technologies | Description |
|---|---|---|
| Causal Engine | Python, EconML, DoWhy | Implements DML and DAGs. |
| Statistical Match | Scikit-learn | Performs propensity score matching. |
| Prescriptive Solver | SciPy Optimization | Allocates personalized discounts within budget limits. |
| Experiment UI | React, Plotly.js | Displays


## 📅 Day 13 — Causal Graphing & Dashboard Scaffolding

**Project:** EconoCausal – Dynamic Pricing Using Double Machine Learning  
**Focus:** DoWhy Causal DAG Implementation & React Dashboard Initialization

### 1. Causal Graphing Using DoWhy

- Used Microsoft's DoWhy library to define a Directed Acyclic Graph (DAG) for a mock retail campaign dataset.
- Identified the key causal variables required for the analysis.
- Defined the treatment, outcome, and potential confounding variables.
- Established the relationships between customer characteristics, promotional discounts, and retail sales.
- Prepared the causal structure to support future causal effect estimation.

### 2. Identification of Causal Variables

The following variables were considered for the mock retail dataset:

| Variable Type | Variables | Description |
|---|---|---|
| Treatment | Discount Amount | Promotional discount assigned to customers |
| Outcome | Sales


## 📅 Day 14 — Double Machine Learning Training & Uplift Visualization

**Project:** EconoCausal – Dynamic Pricing Using Double Machine Learning  
**Phase:** Causal Model Training and Performance Evaluation  
**Technologies:** Python, EconML, Scikit-learn, Random Forest, LightGBM, React, Plotly.js

### 1. Objective
The main objective of Day 14 was to strengthen the EconoCausal causal inference engine by training Double Machine Learning (DML) models and estimating Individual Treatment Effects (ITE).

The work also focused on integrating interactive visualizations to evaluate the performance of the causal model using Qini curves and Uplift charts.

### 2. Double Machine Learning Model Training
- Used the cleaned Online Retail II dataset for causal model training.
- Defined `unit_price` as the treatment variable.
- Defined `quantity` as the outcome variable.
- Selected relevant product, geographical, and time-related variables as confounders.
- Used EconML to implement the Double Machine Learning framework.
- Evaluated Random Forest and LightGBM as potential machine learning base estimators.
- Applied cross-fitting to reduce overfitting and improve estimation reliability.
- Generated Individual Treatment Effects (ITE) to understand how price changes affect purchasing quantity across observations.

### 3. Individual Treatment Effect (ITE) Estimation
ITE estimation helps identify how different observations respond to changes in product prices.

The estimated treatment effects can support:
- Identifying price-sensitive customer and product segments.
- Understanding variations in purchasing behavior.
- Evaluating the impact of price changes on purchase quantity.
- Supporting personalized and data-driven pricing decisions.

### 4. Qini Curves and Uplift Visualization
Integrated Plotly.js into the EconoCausal experimentation dashboard to visualize causal model performance.

**Key visualization components:**
- **Qini Curve:** Evaluates how effectively the model ranks observations based on estimated treatment effects.
- **Uplift Chart:** Displays the estimated incremental impact of a treatment across different targeting groups.
- **Random Baseline:** Provides a benchmark to compare model-guided targeting against random targeting.
- **Model Performance Comparison:** Helps evaluate whether causal model-based targeting provides better results than a random rollout.

### 5. Technology Stack

| Component | Technology |
|---|---|
| Causal Inference | EconML |
| Base Estimators | Random Forest / LightGBM |
| Data Processing | Pandas, NumPy |
| Machine Learning | Scikit-learn |
| Visualization | Plotly.js |
| Frontend | React |
| Programming Language | Python |

### 6. Expected Deliverables
- EconML Double Machine Learning training pipeline.
- Individual Treatment Effect estimation outputs.
- Random Forest and LightGBM estimator configurations.
- Interactive Qini curve visualization.
- Uplift analysis charts with a random targeting baseline.
- Model evaluation outputs for comparing targeting strategies.

### 7. Conclusion
Day 14 focused on advancing the EconoCausal project from initial causal effect estimation toward model evaluation and interactive visualization.

The integration of EconML and


## 📅 Day 15 — Double Machine Learning Training & Uplift Visualization

### 1. Objective

The main objective of Day 15 was to strengthen the EconoCausal causal inference engine by training Double Machine Learning (DML) models using the EconML framework and developing interactive visualizations to evaluate treatment-effect performance.

The implementation focuses on estimating Individual Treatment Effects (ITE) and comparing the performance of a causal targeting strategy against a random rollout strategy.

### 2. Technologies and Libraries Used

- **Python** — Model development and data processing.
- **EconML** — Double Machine Learning and causal effect estimation.
- **Scikit-learn** — Machine learning base estimators.
- **Random Forest / LightGBM** — Base models for nuisance estimation.
- **Pandas & NumPy** — Data manipulation and numerical operations.
- **Plotly.js** — Interactive charts and data visualization.
- **React.js** — Dashboard integration.

### 3. Double Machine Learning Model Training

The EconML framework was used to develop the Double Machine Learning pipeline.

**Key implementation steps:**

1. Loaded the cleaned retail dataset from the preprocessing pipeline.
2. Defined `unit_price` as the treatment variable.
3. Defined `quantity` as the outcome variable.
4. Selected product, geographical, and time-related features as confounding variables.
5. Prepared training and testing datasets.
6. Configured Random Forest or LightGBM as machine learning base estimators.
7. Applied cross-fitting to reduce overfitting and estimation bias.
8. Trained the DML estimator using the selected features.
9. Generated Individual Treatment Effect (ITE) estimates.

### 4. Individual Treatment Effect (ITE) Estimation

ITE estimation helps identify how changes in product prices affect purchasing quantities across individual observations.

**Key benefits:**

- Identifies differences in customer price sensitivity.
- Measures heterogeneous treatment effects.
- Helps understand product-level demand responses.
- Supports personalized dynamic pricing decisions.
- Provides causal insights for business optimization.

### 5. Uplift Analysis Using Plotly.js

Plotly.js was integrated into the project dashboard to visualize the performance of the causal model.

**Visualization components:**

- **Qini Curve:** Measures the cumulative incremental impact of targeting observations based on estimated treatment effects.
- **Uplift Chart:** Visualizes the incremental response achieved through causal targeting.
- **Random Baseline:** Provides a benchmark representing random targeting.
- **Causal Model Performance:** Helps evaluate whether ITE-based targeting performs better than random allocation.

The visual comparison is designed to demonstrate whether the causal model can identify more valuable targeting opportunities than a random rollout.

### 6. Expected Outputs

| Component | Expected Output |
|---|---|
| DML Model | Trained EconML estimator |
| ITE Estimation | Individual treatment-effect values |
| Qini Curve | Cumulative uplift performance |
| Uplift Chart | Targeting effectiveness visualization |
| Random Baseline | Benchmark for comparison |
| React Dashboard | Interactive visualization interface |

### 7. Business Impact

The Day 15 implementation supports the development of an intelligent dynamic pricing system.

- Improves customer-level pricing insights.
- Identifies observations with different treatment responses.
- Helps reduce ineffective promotional spending.
- Supports better pricing and targeting strategies.
- Provides visual evidence for evaluating causal model performance.

### 8. Challenges and Considerations

- Selecting suitable base estimators.
- Managing computational requirements for large datasets.
- Avoiding overfitting during model training.
- Ensuring reliable ITE estimation.
- Correctly calculating Qini and uplift metrics.
- Comparing causal targeting with a fair random baseline.

### 9. Conclusion

Day 15 focused on advancing the EconoCausal project through Double Machine Learning model training and uplift visualization.

The EconML framework provides the foundation for estimating Individual Treatment Effects, while Plotly.js enables interactive visualization of Qini curves and uplift charts.

Together, these components help evaluate causal targeting strategies and support the development of data-driven dynamic pricing solutions.

### 10. Next Steps

- Validate and compare different DML model configurations.
- Improve ITE estimation through hyperparameter tuning.
- Evaluate Qini and uplift performance against suitable baselines.
- Integrate causal model outputs with the budget optimization module.
- Prepare the model for API and dashboard integration.


## Day 16 – Data Cleaning, Preprocessing & DML Dataset Preparation

**Phase:** Data Collection & Preprocessing  
**Date:** October 22, 2026  
**Branch:** `data-prep`  
**Target PR:** `main`  
**Status:** Completed

### 1. Objective

Completed the end-to-end data processing pipeline for the EconoCausal project. The primary objective was to clean, standardize, and prepare the Starbucks datasets and UK Online Retail II (2009–2011) dataset for Double Machine Learning (DML) estimation.

### 2. Key Technical Achievements

#### A. Starbucks Dataset Cleaning
- Standardized and cleaned the `portfolio.json`, `profile.json`, and `transcript.json` datasets.
- Removed duplicate records.
- Converted complex nested data types into string representations for reliable deduplication.
- Handled missing demographic information.

#### B. Online Retail II Dataset Consolidation
- Combined the two yearly datasets into a single unified dataset.
- 2009–2010 dataset: 525,461 rows.
- 2010–2011 dataset: 541,910 rows.
- Prepared the consolidated dataset for causal modeling.

#### C. DML Filtering Pipeline

Applied the following data-cleaning and filtering rules:

- Removed return and cancellation transactions where the invoice number starts with `C`.
- Removed records with `Quantity <= 0`.
- Retained only records with positive unit prices (`unit_price > 0`).
- Removed records with missing `customer_id`.
- Replaced missing product descriptions with `UNKNOWN`.
- Removed exact duplicate rows across all columns.

#### D. Git Large File Storage (LFS)
- Configured Git Large File Storage (LFS).
- Added tracking for large processed CSV files.
- Successfully pushed `cleaned_online_retail_dml.csv` to GitHub without file-size warnings.

### 3. Pipeline Output & Deliverables

Successfully generated the final DML modeling dataset containing **793,609 clean records**.

**Output File:**
`Data/Processed/cleaned_online_retail_dml.csv`

| File Path | Type | Description |
|---|---|---|
| `src/data_preprocessing.py` | Python Script | Automated data-cleaning pipeline and DML exporter |
| `Data/Processed/cleaned_online_retail_dml.csv` | CSV (83.9 MB) | Final DML modeling-ready dataset |
| `.gitattributes` | Git LFS Config | Tracks large CSV files using Git LFS |

### 4. Final Results

- Successfully cleaned and standardized the Starbucks datasets.
- Consolidated the UK Online Retail II datasets.
- Implemented DML-specific filtering rules.
- Generated 793,609 clean records for causal analysis.
- Configured Git LFS for handling large datasets.
- Prepared the dataset for subsequent Double Machine Learning implementation.

### 5. Conclusion

Day 16 successfully completed the data collection, cleaning, and preprocessing stage of the EconoCausal project. The final dataset is now standardized, deduplicated, and ready for Double Machine Learning (DML) estimation and further causal analysis.
