# Roller Coaster Dataset: Exploratory Data Analysis (EDA)

An exploratory data analysis of a roller coaster dataset, built in Python with pandas, Matplotlib and Seaborn. This project was completed as part of my AI/ML programme and covers the EDA stage of the machine learning lifecycle: inspecting, cleaning, visualising and questioning a real-world dataset before any modelling takes place.

## Project Overview
The notebook in this repository analyses `coaster_db.csv`, a dataset of 1,087 roller coasters described by 56 columns, including name, location, manufacturer, type, opening date, speed, height, number of inversions and g-force.

The project does not build a predictive model. Its purpose is to understand the data, what it contains, what problems it has, how each variable is distributed and how the variables relate to one another. The analysis follows five steps:

1. **Data understanding:** importing libraries, loading the data and running an initial audit.
2. **Data preparation:** selecting relevant columns, correcting data types, renaming columns, and handling missing values and duplicates.
3. **Feature understanding:** univariate analysis of individual columns.
4. **Feature relationships:** bivariate and multivariate analysis, including correlation.
5. **Asking questions:** answering a specific question with grouping and aggregation.


## Dataset
File: `coaster_db.csv` 
Raw size: 1,087 rows × 56 columns 
Size after preparation | 990 rows × 13 columns 
Key columns used: Coaster name, location, type, year introduced, opening date, speed (mph), height (ft), inversions, g-force 


## Topics and Techniques Explored
**Data inspection**
- `shape`, `head()`, `columns`, `dtypes` and `describe()` for an initial audit
- Reading summary statistics to spot unrealistic values

**Data preparation**
- Selecting columns and creating an independent copy with `.copy()`
- Converting data types with `pd.to_datetime()`
- Renaming columns with `rename()`
- Counting missing values with `isnull().sum()`
- Detecting duplicates with `duplicated()`, including near-duplicates that an exact-row check misses
- Removing duplicates using a subset of columns and resetting the index

**Univariate analysis**
- `value_counts()` and bar charts for counting categories and years
- Histograms and KDE plots for the distribution of a continuous variable
- 
**Bivariate and multivariate analysis**
- Scatter plots in pandas and Seaborn
- Adding a third variable with colour (`hue`)
- Pair plots across several variables
- Correlation matrices and heatmaps


**Aggregation and questioning the data**
- Filtering with `query()`
- `groupby()` and `agg()` for per-group statistics
- Sorting and horizontal bar charts to present results


**How to navigate:**
- Start with **this README** for the overview.
- Open **`Roller Coaster Exploratory Data Analysis.ipynb`** to see the code, outputs and charts, in the order of the five steps above.
- Read **`Roller_Coaster_EDA_Writeup.md`** for a full explanation of each concept, the reasoning behind each decision, how the work connects to the wider programme, and my reflections.

### Requirements
- Python 
- pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook


## Key Takeaways
- **Real data is messy.** The dataset contained text mixed with units, columns with hundreds of missing values, and duplicate records. EDA is what exposes these problems before they affect results.
- **Check for duplicates in more than one way.** An exact-row check found nothing, but checking by coaster name revealed 97 near-duplicates, such as the same ride recorded with opening years one year apart. Removing them brought the dataset from 1,087 to 990 rows.
- **Missing data is a finding in itself.** Only 171 coasters had a `Height_ft` value, so any result involving height rests on a small part of the dataset.
- **Speed, height and g-force move together.** Speed and height correlate at about 0.73, and speed and g-force at about 0.61. The number of inversions has almost no relationship with speed.
- **Coaster building peaked around 1999 and 2000**, with 46 and 45 coasters introduced in those years.
- **Speed is roughly bell-shaped**, with most coasters between 30 and 70 mph and a few extreme outliers reaching about 149 mph.
- **Location matters, if you filter carefully.** Excluding the catch-all "Other" category and requiring at least 10 coasters per park, Busch Gardens Williamsburg and Cedar Point had the highest average speeds (about 58 mph), while Alton Towers had the lowest (about 43 mph).
- **Correlation is not causation**, and it only captures straight-line relationships.
- **EDA feeds directly into modelling.** Missing values, correlated features and outliers all shape later decisions in feature engineering and model building.

## Author
**Olajide Emmanuel**
