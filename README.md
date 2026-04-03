# Data-Cleaning-In-Machine-Learning

# Data Cleaning and Manipulation Notebook

This Google Colab notebook demonstrates various data cleaning and manipulation techniques using the `pandas` library in Python. It processes three different datasets: Olympics data, a log file, and FIFA player data, applying common data preparation steps.

## Table of Contents

-   [Project Description](#project-description)
-   [Datasets Used](#datasets-used)
-   [Setup](#setup)
-   [Key Operations Performed](#key-operations-performed)
-   [Usage](#usage)

## Project Description

This notebook serves as an example of practical data cleaning workflows. It covers:

1.  **Initial Data Inspection**: Loading data, viewing head/tail, summary statistics, data types, and null value counts.
2.  **Column Renaming**: Standardizing column names for better readability and usability.
3.  **Indexing and Multi-indexing**: Setting and resetting DataFrame indices, including creating multi-level indices.
4.  **Handling Missing Values**: Using `dropna()` and `fillna()` with different methods (`ffill`, `bfill`) to manage missing data.
5.  **Boolean Masking**: Filtering data based on conditions.
6.  **Removing Duplicates**: Identifying and eliminating duplicate rows.
7.  **Feature Selection**: Dropping irrelevant columns and rows based on criteria.

## Datasets Used

The notebook utilizes the following CSV files, which are assumed to be mounted from Google Drive at `/content/drive/MyDrive/Untitled folder/`:

*   `olympics.csv`: Contains historical Olympics medal data.
*   `log.csv`: A sample log file with timestamped user activity.
*   `fifa_cleaned.csv`: Detailed FIFA player statistics.

## Setup

To run this notebook, you will need the following libraries installed:

```bash
pip install pandas
```

Ensure your Google Drive is mounted in Colab to access the datasets. The datasets are expected to be in the path `/content/drive/MyDrive/Untitled folder/`.

```python
from google.colab import drive
drive.mount('/content/drive')
```

## Key Operations Performed

### Olympics Data (`df`)

-   Loaded `olympics.csv`, skipping the first row and setting the first column as the index.
-   Renamed columns for clarity (e.g., `01 !` to `Gold`).
-   Applied boolean masking to filter for countries with gold medals.
-   Dropped rows with `NaN` values from the masked DataFrame.
-   Demonstrated setting and resetting single and multi-level indices (`Gold`, `Gold.1`).

### Log Data (`df1`)

-   Loaded `log.csv`.
-   Set the `time` column as the index and sorted by index.
-   Dropped rows with any `NaN` values.
-   Demonstrated `fillna()` with `ffill` (forward fill) and `bfill` (backward fill) methods (though after dropping NaNs, these might not have a visible effect on the small, already cleaned result).

### FIFA Data (`df2`)

-   Loaded `fifa_cleaned.csv`.
-   Set the `id` column as the index and sorted by index.
-   Dropped columns with more than 50% missing values (`threshold = 0.5 * len(df)`).
-   Dropped rows where 'name' or 'overall_rating' were `NaN`.
-   Removed duplicate rows.
-   Filtered players whose age is less than 30 and play in the 'ST' (Striker) position.

## Usage

Simply run the cells sequentially in the Google Colab environment. Each section of the notebook focuses on a different dataset and demonstrates specific data cleaning techniques. The output of each step is displayed to show the transformation of the data.

This notebook is suitable for users looking to understand basic to intermediate data cleaning and manipulation techniques in pandas.
```
