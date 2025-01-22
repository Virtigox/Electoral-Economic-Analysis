```Cite Dataset
@data{DVN/42MVDX_2017,
author = {MIT Election Data and Science Lab},
publisher = {Harvard Dataverse},
title = {{U.S. President 1976–2020}},
UNF = {UNF:6:F0opd1IRbeYI9QyVfzglUw==},
year = {2017},
version = {V8},
doi = {10.7910/DVN/42MVDX},
url = {https://doi.org/10.7910/DVN/42MVDX}
}
```

```Cite Dataset
author = {Breau of Economic Analysis},
publisher = {U.S. Department of Commerce},
title = {{SASUMMARY State annual summary statistics: personal income, GDP, consumer spending, price indexes, and employment}},
year = {2023},
url {https://www.bea.gov/}
}
```

### **1. Overview of the Datasets**

- **BEA State Annual Summary Statistics**:
    
    - Includes data on personal income, GDP, consumer spending, price indices, and employment by state.
    - Likely provides economic growth metrics.
- **U.S. Presidential Election Results (1976–2020)**:
    
    - Contains state-by-state voting results for presidential elections from 1976 to 2020.
    - Includes data such as vote counts, percentages, and winning candidates.

---

### **2. Project Objective**

Investigate the relationship between a state's economic growth (measured via GDP, employment, etc.) and its voting behavior in presidential elections.

### **3. Data Preparation**M

#### **Data Cleaning**

- **Election Data**:
    - Focus on state-level results for simplicity.
    - Extract variables: state, year, party of winning candidate, vote percentages.
- **BEA Data**:
    - Focus on state and year-level data.
    - Extract economic indicators: GDP, employment, personal income growth, etc.

#### **Data Integration**

- Merge the two datasets on `state` and `year` as common keys.
- Handle any mismatches in state names (e.g., abbreviations vs. full names).

---

### **4. Exploratory Data Analysis (EDA)**

#### Questions to Explore:

1. How do economic indicators correlate with voting patterns over time?
2. Are there consistent trends in states that vote for a specific party?
3. Do states with higher GDP growth or employment rates lean toward a specific party?

#### Visualizations:

- Time-series plots of GDP/employment trends alongside election results by state.
- Scatter plots showing correlations between economic indicators and vote percentages.
- Heatmaps to show party preferences geographically with economic metrics.

---

### **5. Analysis**

#### Hypotheses to Test:

- Economic growth in a state positively/negatively correlates with voting for a specific party.
- States with higher income levels tend to vote consistently for one party.

#### Statistical Tests:

- Correlation analysis (Pearson or Spearman) between economic indicators and election outcomes.
- Regression analysis to model the impact of economic factors on voting outcomes.

---

### **6. Tools**

- **Python Libraries**:
    - `pandas` and `numpy` for data cleaning and merging.
    - `matplotlib` and `seaborn` for visualizations.
    - `scipy.stats` or `statsmodels` for statistical analysis.
- **Jupyter Notebook** for documenting and running your analysis interactively.

---

### **7. Final Deliverables**

- **Report**: Summarize key findings, visualizations, and interpretations.
- **Dashboard** (Optional): Use tools like Tableau or Power BI to create an interactive visualization of your analysis.

# CODE
```Python
import pandas as pd

# Load the csv file
gdp_data = pd.read_csv('/workspaces/My_Vault/electoral_analysis/state_gdp_data.csv')


# Extract the unique states from the GeoName column
unique_states = gdp_data['GeoName'].unique()
# Count the number of unique states
num_unique_states = len(unique_states)
print(f"Number of unique states in GeoName: {num_unique_states}")
print(unique_states)



# Load the csv file

bea_data = pd.read_csv('/workspaces/My_Vault/electoral_analysis/bea_data.csv', skiprows=3)

# Drop the 'GeoFips' and 'LineCode' columns
bea_data = bea_data.drop(columns=['GeoFips', 'LineCode'])
# Dictionary to map original descriptions to concise descriptions
description_mapping = {

'Real GDP (millions of chained 2017 dollars) 1': 'Real GDP',

'Real personal income (millions of constant (2017) dollars) 2': 'Real Personal Income',

'Real PCE (millions of constant (2017) dollars) 3': 'Real PCE',

'Per capita personal income 6': 'Per Capita Personal Income',

'Per capita disposable personal income 7': 'Per Capita Disposable Personal Income',

'Total employment (number of jobs)': 'Total Employment'

}

# Strip any leading or trailing whitespace from the 'Description' column

bea_data['Description'] = bea_data['Description'].str.strip()  

# Filter the DataFrame to only include rows with descriptions that match the keys in the description_mapping dictionary

bea_data = bea_data[bea_data['Description'].isin(description_mapping.keys())]

# Replace the descriptions with the concise descriptions

bea_data['Description'] = bea_data['Description'].replace(description_mapping)

gdp_data = bea_data

# Print the first few rows to verify the changes

print(gdp_data.head())

  

df = pd.DataFrame(gdp_data)

  

print(df)

# Define the presidential administrations

administrations = {

'Clinton': (1993, 2000),

'Bush': (2001, 2008),

'Obama': (2009, 2016),

'Trump': (2017, 2020),

'Biden': (2021, 2023) # Assuming data is available up to 2023

}

  

# Function to calculate year-over-year growth rates

def calculate_annual_growth(values):

growth_rates = []

# Calculate year-over-year growth

for i in range(1, len(values)):

start_value = values[i - 1]

end_value = values[i]

# Skip calculation if start_value or end_value is NaN

if pd.isna(start_value) or pd.isna(end_value):

continue

# Growth rate formula

growth_rate = ((end_value - start_value) / start_value) * 100

growth_rates.append(growth_rate)

return growth_rates

  

# Function to calculate overall growth rate for a given term

def calculate_overall_growth(start_value, end_value):

if pd.isna(start_value) or pd.isna(end_value):

return None

# Overall growth rate formula

overall_growth_rate = ((end_value - start_value) / start_value) * 100

return overall_growth_rate

  

# Convert year columns to numeric

year_columns = [col for col in gdp_data.columns if col.isdigit()]

gdp_data[year_columns] = gdp_data[year_columns].apply(pd.to_numeric, errors='coerce')

  

# Add new columns for each administration's average and overall growth rates

for admin, (start_year, end_year) in administrations.items():

gdp_data[f'{admin} Avg Growth Rate'] = None

gdp_data[f'{admin} Overall Growth Rate'] = None

for index, row in gdp_data.iterrows():

# Extract the values for the specified years

years = [str(year) for year in range(start_year, end_year + 1) if str(year) in gdp_data.columns]

if len(years) < 2:

continue

values = row[years].values

# Calculate the annual growth rates for the term

annual_growth_rates = calculate_annual_growth(values)

# Calculate the average growth rate for the term

if annual_growth_rates:

avg_growth_rate = sum(annual_growth_rates) / len(annual_growth_rates)

gdp_data.at[index, f'{admin} Avg Growth Rate'] = avg_growth_rate

# Calculate the overall growth rate for the term

overall_growth_rate = calculate_overall_growth(values[0], values[-1])

gdp_data.at[index, f'{admin} Overall Growth Rate'] = overall_growth_rate

  

# Print the first few rows to verify the changes

print(gdp_data.head())

pd.DataFrame(gdp_data).to_csv('/workspaces/My_Vault/electoral_analysis/State_Economic_Grwoth_Rate_data.csv', index=False)

```


