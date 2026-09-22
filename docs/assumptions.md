# Analytical Assumptions and Data Limitations

1. **Transaction Independence:**
   Each row is assumed to represent a completely independent order.

2. **Unified Currency Scale:**
   Although the raw data contains both dollar (`$`) and rupee (`Rs.`) symbols, a specific exchange rate is not available in the dataset. Therefore, after cleaning, all financial values will be treated as being on a common international currency scale.

3. **Outlier Thresholds:**
   Values such as `Qty = 9999` or `Unit Price > 50000` will be identified as possible data-entry errors and excluded from normal retail analysis.

4. **Missing Return Status:**
   For missing values (`NaN` or blanks) in the `Returned?` column, the values will not be directly assumed to mean `No`. Instead, the data will first be analyzed to determine whether the customer actually made a return request.
