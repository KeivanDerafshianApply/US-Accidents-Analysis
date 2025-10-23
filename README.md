# US Accidents Analysis (2016-2023) 🚗💥

This project analyzes the extensive US Accidents dataset (2016-2023) from Kaggle to identify patterns and contributing factors related to traffic accidents across the United States. The primary focus is on exploring temporal trends, geographical hotspots, and the influence of weather conditions.

Due to the dataset's large size (millions of records), this analysis uses Python (Pandas, Matplotlib, Seaborn) for **sampling, cleaning, and aggregation**. The processed, aggregated data is then exported, ready for in-depth visualization and dashboard creation in **Tableau**.

## Project Goal

My aim was to answer questions like:
* When do most accidents occur (time of day, day of week, month)?
* Where are the major accident hotspots geographically (by state/county)?
* How do weather conditions (precipitation, visibility, temperature) correlate with accident frequency or severity?
* Can we create a manageable, aggregated dataset that retains key insights for effective visualization?

## Data

The dataset `US Accidents (2016 - 2023)` is sourced from [Kaggle](https://www.kaggle.com/datasets/sobhanmoosavi/us-accidents) and downloaded directly using the `kagglehub` library. It contains detailed information on each accident, including:
* **Time:** `Start_Time`, `End_Time`
* **Location:** `Start_Lat`, `Start_Lng`, `City`, `County`, `State`, `Zipcode`
* **Conditions:** `Weather_Condition`, `Temperature(F)`, `Visibility(mi)`, `Precipitation(in)`, etc.
* **Road Features:** `Traffic_Signal`, `Crossing`, `Junction`, `Stop`, etc.
* **Severity:** `Severity` (an integer from 1 to 4)

## Methodology

1.  **Data Loading & Sampling (Python - Pandas, KaggleHub):**
    * Downloaded the dataset using `kagglehub`.
    * Loaded the data, parsing date/time columns.
    * **Crucially, sampled the data (e.g., 1 million records or specific years) due to its massive size to make processing feasible.** *Initial exploration confirmed the dataset size necessitated sampling for this analysis.*
    * Performed initial cleaning: addressed missing values in key columns (like weather or location), corrected data types.

2.  **Exploratory Data Analysis (Python - Pandas, Matplotlib, Seaborn):**
    * Analyzed accident frequency over time (hourly, daily, monthly trends).
    * Examined the distribution of accidents by state and severity.
    * Investigated the most common weather conditions during accidents.

3.  **Feature Engineering & Aggregation (Python - Pandas):**
    * Extracted time features: `Hour`, `DayOfWeek`, `Month`, `Year`.
    * Simplified weather conditions into broader categories (e.g., 'Clear', 'Rain', 'Snow', 'Fog').
    * **Aggregated the data:** Grouped accidents by relevant dimensions (e.g., `State`, `County`, `Year`, `Month`, `Hour`, `Weather_Category`, `Severity`) to count occurrences and calculate average conditions. This step is vital to reduce data size for Tableau while preserving analytical potential.

4.  **Data Export (Python - Pandas):**
    * Saved the aggregated DataFrame to `output/us_accidents_agg_tableau.csv`.

5.  **Visualization (Tableau - Suggested):**
    * Connected the `output/us_accidents_agg_tableau.csv` to Tableau.
    * **Dashboards:**
        * **Overview:** KPIs (Total Accidents in sample), Map of accidents by State/County, Trend lines (Monthly/Yearly).
        * **Time Analysis:** Heatmap of accidents by Day of Week vs. Hour, Monthly accident trends.
        * **Weather Impact:** Map colored by average severity under different weather conditions (using filters), Bar charts showing accident counts by weather category and severity.
        * **Geospatial Hotspots:** Density map showing accident concentration (using State/County and counts).

## Key Findings (Example - Fill with your own!)

* Accidents peak during afternoon commute hours (around 3-6 PM) on weekdays.
* California, Florida, and Texas show the highest accident counts in the sampled data.
* While 'Clear' weather has the most accidents overall (likely due to being the most common condition), the *rate* or *severity* might be higher during adverse conditions like rain or fog (further investigation in Tableau needed).
* (Add more specific findings based on your EDA and Tableau dashboards).

## How to Run

1.  **Clone the repository:**
    ```bash
    git clone <your-repo-url>
    cd us-accidents-analysis
    ```
2.  **Set up Kaggle API Token:** Ensure `kaggle.json` is configured.
3.  **Set up Python environment:**
    ```bash
    pip install -r requirements.txt
    ```
4.  **Run the Jupyter Notebook:** `us_accidents_analysis.ipynb`. This downloads the data, samples it, performs analysis, and generates `output/us_accidents_agg_tableau.csv`. **Note:** Downloading and initial loading might take some time depending on your connection and machine specs.
5.  **Visualize in Tableau:** Connect to the `output/us_accidents_agg_tableau.csv` in Tableau Desktop.

## Tools Used

* **Python:** Pandas, NumPy, Matplotlib, Seaborn, KaggleHub
* **Tableau Desktop**
* **Jupyter Notebook**
