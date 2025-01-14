# ETL Process for HR Analytics for Attrition and Performance

This section outlines the **ETL (Extract, Transform, Load)** process used in the project **"HR Analytics for Attrition and Performance."**

## 1. Extract: Importing Data

In the first phase of the ETL process, various datasets were imported into Power BI for analysis:

- The following datasets were loaded into Power BI:
  - **Education**
  - **Attrition Rates**
  - **Employee Data 2018 - 2019**
  - **Job Involvement**
  - **Performance Rating**
  - **Satisfaction**
  - **WorkLifeBalance**
  - **Measure**

These tables serve as the raw data, providing a variety of employee-related information such as demographics, performance metrics, satisfaction, and attrition rates.

## 2. Transform: Data Cleaning and Transformation

Once the data was extracted and loaded into Power BI, the transformation process began. This phase involved cleaning and structuring the data to make it ready for analysis. Key transformation steps include:

### Data Cleaning
- **Identified and removed** missing values and incorrect formats.
- **Removed blank rows** from the `Attrition Rates` table.
- The `Employee Data` table underwent specific transformations:
  - **Removed blank rows** and irrelevant columns.
  - **Converted "Monthly income (Lacs)"** from a value in lacs to actual currency (rupees) by multiplying by 100,000 and appending the currency symbol (`Rupees`).
  - Added a **conditional column for `AgeGroup`** to categorize employees into different age ranges (e.g., `<20 years`, `20-30 years`, etc.).

#### Example of Data Transformation:
- The **Monthly Income** column was adjusted to reflect values in rupees by multiplying the `"Lacs"` values by `100,000`, then the column was renamed to `"Monthly Income"` with the currency symbol added.

### Calculated Columns and Measures
- **`AgeGroup`**: Created a **conditional column** to group employees based on age ranges. This transformation was essential for demographic analysis.
- Created **DAX formulas** to derive key metrics and calculated fields:
  - **`% Attrition`**: A measure to calculate employee attrition percentages.
  - **`Active Employees`**: A measure that tracks the count of employees who are currently active.
  - **`Inactive Employees`**: A measure for counting employees who have left the organization.
  - **`Total Employees`**: A measure to calculate the total number of employees in the dataset.

## 3. Load: Data Modeling and Relationships

After the data was cleaned and transformed, the next phase involved loading the data into the Power BI model and establishing relationships between tables for efficient analysis.

### Data Modeling
- The model was **optimized** by ensuring correct relationships between tables. This allows for accurate reporting and visualization by linking tables using common fields.
- **Relationships** were established between different datasets:
  - Linked **`Education`** to **`Employee Data`** using the **`Education ID`**.
  - Linked **`Job Involvement`** to **`Employee Data`** using the **`Job Involvement ID`**.
  - Linked **`Satisfaction`** to **`Employee Data`** using the **`Satisfaction ID`**.
  - Linked **`Performance Rating`** to **`Employee Data`** using the **`Performance ID`**.
  - Linked **`WorkLifeBalance`** to **`Employee Data`** using the **`WorkLifeBalance ID`**.

### Hierarchies
- A **Department Hierarchy** was created to enable drill-down analysis. The hierarchy was created by expanding the **`Employee Data 2018-2019`** table, then linking **Department** to **Job Role**.
- This hierarchy allows for analyzing data at different levels, such as department-level overviews, and drilling down into specific roles within departments.

### Optimizing Relationships
- Ensured that the relationships were configured correctly for optimal performance. This involved ensuring that the relationships were set to **single or bi-directional** depending on the specific needs of the analysis.

## Key ETL Steps Summary

1. **Extract**: Imported datasets like `Education`, `Attrition Rates`, `Employee Data`, `Job Involvement`, etc., into Power BI.
2. **Transform**:
   - Cleaned the data by removing null/blank values, formatting errors, and irrelevant columns.
   - Created calculated columns and DAX measures to derive insights such as `age group` categorization, employee `attrition rate`, and income conversion.
3. **Load**: 
   - Established relationships between the tables to facilitate accurate reporting and analysis.
   - Built hierarchies (e.g., `Department -> Job Role`) for drill-down analysis.
   - Optimized data model by configuring relationships appropriately.

## Conclusion
The **ETL process** in this project played a crucial role in preparing the HR data for analysis and visualization. By cleaning, transforming, and establishing relationships between the data, meaningful insights could be derived. These insights were visualized through Power BI, helping HR managers understand patterns in employee attrition, performance, and satisfaction.
