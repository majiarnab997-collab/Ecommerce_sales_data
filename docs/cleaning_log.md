# Data Cleaning Audit Log

| Log ID | Column Affected | Issue Identified                                           |  Rows Affected  | Decision / Transformation                             | Reason & Statistical Impact                                                                   |
| :----: | :-------------- | :--------------------------------------------------------- | :-------------: | :---------------------------------------------------- | :-------------------------------------------------------------------------------------------- |
| LOG-01 | `Qty`           | Numbers stored as text (e.g., `"five"`)                    | Subject to scan | Convert string values to integers                     | Numeric values are required for mathematical calculations such as sum and mean                |
| LOG-02 | `Qty`           | Negative values (e.g., `-5`, `-3`)                         | Subject to scan | Remove the row or verify using absolute value (`Abs`) | Product quantity cannot normally be negative                                                  |
| LOG-03 | `Qty`           | Unrealistic outliers (e.g., `9999`)                        | Subject to scan | Filter or remove outliers                             | Extreme values can significantly distort the mean and distribution                            |
| LOG-04 | `Unit Price`    | Currency symbols (e.g., `"$"`, `"Rs."`)                    | Subject to scan | Remove symbols using Regex and convert to float       | Statistical calculations require numeric/float values                                         |
| LOG-05 | `Unit Price`    | Text values (e.g., `"free"`)                               | Subject to scan | Assign `0.0` or drop the row                          | Free items can affect revenue calculations                                                    |
| LOG-06 | `Returned?`     | Inconsistent formats (`1`, `0`, `Y`, `N`, `True`, `False`) | Subject to scan | Map values to binary format (`1 = Yes`, `0 = No`)     | A consistent binary format is required for Bernoulli distribution and logistic calculations   |
| LOG-07 | `Order Date`    | Multiple date formats and `"invalid_date"`                 | Subject to scan | Convert to a standardized datetime format             | A consistent datetime format is required for time-series analysis and time-based calculations |




| Log ID | Column Affected | Issue Identified | Rows Affected | Decision / Transformation | Reason & Statistical Impact |
| :----: | :-------------- | :--------------- | :-----------: | :------------------------ | :-------------------------- |
| LOG-07 | `Order Date` | Multiple date formats and `"invalid_date"` | Subject to scan | Convert to a standardized datetime format | A consistent datetime format is required for time-series analysis and time-based calculations |
| LOG-08 | Column Names | No leading or trailing spaces were found in the column names | 0 | No transformation required | Column names are already properly formatted, so no cleaning is necessary |
| LOG-09 | All Columns | Completely empty row found at index `159` | 1 | Remove row at index `159` | A completely empty row contains no useful information and can affect row counts and data quality checks |


## Missing Value Analysis

The dataset was checked for both standard missing values and disguised missing-value markers such as `unknown`, `N/A`, `n/a`, `invalid_date`, and `nan`.

### Columns with Higher Missing Rates

The following columns have a missing-value rate above 5%:

| Column | Total Missing | Missing Percentage |
| :--- | ---: | ---: |
| `Product Name` | 93 | 9.02% |
| `Country` | 194 | 18.82% |
| `PaymentMethod` | 233 | 22.60% |
| `customer_email` | 103 | 9.99% |
| `Rating` | 62 | 6.01% |
| `Discount` | 124 | 12.03% |

These columns require further investigation and an appropriate missing-value treatment before statistical analysis.

### Disguised Missing Values

The dataset was also scanned for disguised missing-value markers, including:

- `unknown`
- `N/A`
- `n/a`
- `invalid_date`
- `nan`

The number of occurrences for each marker was recorded during the cleaning process and will be handled consistently during the missing-value treatment stage.