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

