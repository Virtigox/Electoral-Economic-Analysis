
### **Creating and Manipulating DataFrames**

- `pd.DataFrame()` – Create a DataFrame.
- `pd.Series()` – Create a Series.

### **Viewing and Inspecting Data**

- `.head(n)` – View the first `n` rows.
- `.tail(n)` – View the last `n` rows.
- `.info()` – Display DataFrame info (e.g., column types, non-null counts).
- `.shape` – Get the dimensions of the DataFrame (rows, columns).
- `.describe()` – Generate summary statistics for numerical columns.
- `.dtypes` – Get data types of each column.

### **Selecting and Filtering Data**

- `.loc[]` – Label-based indexing (rows and columns).
- `.iloc[]` – Integer-based indexing.
- `.at[]` – Access a single value by label.
- `.iat[]` – Access a single value by position.
- `.query()` – Query the DataFrame using a string expression.
- `.isin()` – Filter based on a list of values.

### **Sorting and Ordering**

- `.sort_values(by, ascending=True)` – Sort by one or more columns.
- `.sort_index()` – Sort by row or column index.

### **Modifying Data**

- `.assign()` – Add or modify columns.
- `.rename()` – Rename columns or index labels.
- `.drop()` – Drop rows or columns.
- `.set_index()` – Set a column as the index.
- `.reset_index()` – Reset the index to default integers.

### **Handling Missing Data**

- `.isnull()` / `.notnull()` – Detect missing or non-missing values.
- `.fillna(value)` – Fill missing values with a specified value.
- `.dropna()` – Remove rows or columns with missing values.

### **Aggregation and Grouping**

- `.groupby()` – Group data by one or more columns.
- `.agg()` – Apply multiple functions to grouped data.
- `.mean()` / `.sum()` / `.count()` / `.max()` / `.min()` – Aggregation methods.
- `.apply()` – Apply custom functions row-wise or column-wise.

### **Merging and Joining**

- `pd.concat()` – Concatenate DataFrames along rows or columns.
- `pd.merge()` – Merge two DataFrames based on keys.
- `.join()` – Join DataFrames on their index.

### **Working with Dates**

- `.to_datetime()` – Convert data to datetime format.
- `.dt` – Access datetime properties (e.g., `.dt.year`, `.dt.month`).
- `.resample()` – Resample time series data (e.g., to daily, monthly frequency).

### **Pivoting and Reshaping**

- `.pivot()` – Reshape data based on column values.
- `.pivot_table()` – Create a pivot table with aggregation.
- `.melt()` – Unpivot DataFrame from wide to long format.
- `.stack()` / `.unstack()` – Reshape DataFrames using the index.

### **File Input/Output**

- `pd.read_csv()` – Read a CSV file into a DataFrame.
- `pd.to_csv()` – Write a DataFrame to a CSV file.
- `pd.read_excel()` / `pd.to_excel()` – Read/write Excel files.
- `pd.read_json()` / `pd.to_json()` – Read/write JSON files.
- `pd.read_sql()` / `pd.to_sql()` – Read/write data to a SQL database.

### **Statistical Methods**

- `.corr()` – Compute pairwise correlation.
- `.cov()` – Compute pairwise covariance.
- `.rank()` – Rank values in a DataFrame or Series.
- `.value_counts()` – Count unique values in a Series.****