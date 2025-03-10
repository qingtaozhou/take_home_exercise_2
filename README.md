# Medical Claims Price Discrepancy Analysis

This repository contains a set of Python scripts and a Jupyter Notebook developed on Google Colab. The project aims to analyze pricing data by comparing standard charges with negotiated rates to identify potential discrepancies in medical pricing. The analysis integrates data from hospital and insurer sources, cleans and unifies the datasets, and applies various discrepancy detection approaches using Python libraries including **NumPy** and **pandas**.

---

## Hypothesis

Records that are **common in both datasets** represent the **same medical procedure** performed at the **same hospital**, covered by the **same insurance payer**. These records appear in **two separate sources**:
- **Insurer’s price transparency files**
- **Hospital’s price transparency files**

### Potential Limitations:
- The comparison might be limited to just **three key columns**:
  - **CPT/HCPCS code** (procedure identifier)
  - **EIN** (hospital tax ID)
  - **Insurancer**
- If **time permits**, additional fields such as:
  - **Provider ID**  
  - **Insurance Plan**
  - **CPT Type**
  can be explored to further **enhance matching accuracy** between the datasets.


## Overview of the Approach

1. **Data Loading & Setup:**
   - Mount Google Drive to access CSV files containing hospital and payer data.
   - Use **pandas** for data manipulation and **NumPy** for numerical operations.

2. **Data Understanding & Integration:**
   - Explore the datasets to understand their structure and identify common fields.
   - Standardize field names across datasets through column renaming.
   - Merge the datasets on key columns (e.g., `payer_name`, `code`, and `ein`).

3. **Data Cleaning:**
   - Correct formatting inconsistencies (e.g., removing dashes from identification numbers).
   - Clean price columns by removing symbols (such as commas and dollar signs) and convert them to numeric types using **pandas** functions.

4. **Discrepancy Evaluation:**
   - **Standard Charges vs. Negotiated Rates:** Compare these values to assess pricing variations.
   - **Frequent Values Comparison:** Evaluate the common (frequent) values for negotiated rates and standard charges across the same CPT code, hospital, and insurer.
   - **Alternative Methods:** Apply maximum/minimum variation analysis and a two-standard deviation threshold to further classify discrepancies.

5. **Visualization & Further Analysis:**
   - Use the cleaned and merged data for visualization and detailed exploration of pricing discrepancies.
   - Leverage **NumPy** for numerical calculations and **pandas** for generating summary statistics.

---

## How to Run the Code

### Prerequisites
- **Google Colab:** The project is designed to run on Google Colab. Ensure you have a Google account.
- **Data Files:** Upload the following CSV files to your Google Drive (or adjust the file paths in the notebook):
  - `hpt_extract_20250213.csv` (Hospital Price Transparency Data)
  - `tic_extract_20250213.csv` (Payer/Insurer Data)
- **Python Libraries:** The analysis uses **NumPy** and **pandas**. These libraries are pre-installed in Google Colab.

### Steps
1. **Mount Google Drive:**
   - Open the provided Jupyter Notebook (e.g., `take-home-exercise-2.ipynb`) in Google Colab.
   - Run the cell that mounts your Google Drive:
     ```python
     from google.colab import drive
     drive.mount('/content/drive')
     ```

2. **Run the Notebook:**
   - Execute the notebook cells sequentially to load, clean, integrate, and analyze the data.
   - The notebook includes sections for exploratory data analysis, merging of datasets, and price discrepancy evaluation.

3. **Review the Results:**
   - Output cells display key findings.

---

## Additional Information
  
- **Discrepancy Analysis Approaches:**  
  - Median-based analysis and a two-standard deviation threshold for a more robust detection of outliers.

- **Extensibility:**  
  Additional analyses (e.g., insurance plan variations or provider-specific pricing) can be integrated by extending the provided functions and analysis steps.

- **Visulization:**  
  -  Explore the  plots and tables for further insights into the data from the output results.

- **Feedback & Improvements:**  
  Contributions and suggestions for improving the analysis are welcome. Feel free to open an issue or submit a pull request.

---
