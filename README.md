# 🧹FIFA 21 Data Cleaning Project Using Python

## Project Overview

This project focuses on cleaning and standardizing the FIFA 21 player dataset obtained from Kaggle. The raw data contains inconsistencies in formatting, special characters, and mixed units of measurement that need to be addressed before any meaningful analysis can be performed.

## Dataset Information

**Source:** Kaggle

**File:** `fifa21 raw data v2.csv`

The dataset contains comprehensive information about FIFA 21 players including their physical attributes, market values, wages, club information, and various player statistics.

## Technologies Used

- **Python 3.13**
- **pandas** - Data manipulation and analysis

## Project Structure

```

├── cleaning.ipynb              # Jupyter notebook with cleaning code
├── fifa21 raw data v2.csv      # Raw dataset (input)
└── fifa21_clean_data.csv       # Cleaned dataset (output)
```

## Data Cleaning Process

### 1. **Initial Setup**
- Imported pandas library
- Loaded the dataset with `low_memory=False` to handle mixed data types
- Configured display options to show all columns

### 2. **Column Management**
- Removed unnecessary columns: `photoUrl` and `playerUrl`
- Removed duplicate rows to ensure data integrity

### 3. **Text Standardization**
- Stripped whitespace and special characters from the `Club` column

### 4. **Height Standardization**
- **Issue:** Mixed formats (feet/inches and centimeters)
- **Solution:** Converted all imperial measurements (e.g., 5'11") to metric (cm)
- **Conversion:** feet × 30.48 + inches × 2.54

### 5. **Weight Standardization**
- **Issue:** Mixed formats (pounds and kilograms)
- **Solution:** Converted all pound measurements (lbs) to kilograms
- **Conversion:** pounds × 0.4535924

### 6. **Value Column Cleaning**
- Removed currency symbols (€)
- Converted abbreviated values:
  - 'M' (millions) → multiplied by 1,000,000
  - 'K' (thousands) → multiplied by 1,000
- Converted to numeric type for calculations

### 7. **Wage Column Cleaning**
- Removed currency symbols and 'K' suffix
- Converted all values to actual amounts (multiplied by 1,000)
- Converted to numeric type

### 8. **Release Clause Column Cleaning**
- Removed currency symbols
- Converted abbreviated values (M and K) to actual amounts
- Handled zero values appropriately
- Converted to numeric type

### 9. **Hits Column Cleaning**
- Filled null values with '0'
- Converted 'K' suffix values (thousands) to actual numbers
- Converted to integer type

### 10. **Loan Date End Column**
- Filled null values with 'Not On Loan' label for clarity

### 11. **Rating Columns Cleaning**
- Cleaned special characters (★) from:
  - `W/F` (Weak Foot rating)
  - `SM` (Skill Moves rating)
  - `IR` (International Reputation)
- Converted all to integer type

## Key Features

✅ Comprehensive data standardization  
✅ Unit conversion (imperial to metric)  
✅ Currency value normalization  
✅ Special character removal  
✅ Null value handling  
✅ Data type optimization  
✅ Duplicate removal  

## Output

The cleaned dataset is exported as `fifa21_clean_data.csv` with:
- UTF-8-SIG encoding for proper character handling
- No index column
- Consistent formatting across all columns
- Ready for analysis and visualization

## How to Use

1. **Clone or download the project files**

2. **Install required libraries:**
   ```bash
   pip install pandas
   ```

3. **Place the raw dataset:**
   - Download the FIFA 21 dataset from Kaggle
   - Place `fifa21 raw data v2.csv` in the project directory

4. **Run the notebook:**
   ```bash
   jupyter notebook cleaning.ipynb
   ```

5. **Execute all cells** to generate the cleaned dataset

## Data Quality Improvements

| Aspect | Before | After |
|--------|--------|-------|
| Height | Mixed (5'11", 180cm) | Standardized (cm) |
| Weight | Mixed (165lbs, 75kg) | Standardized (kg) |
| Value | €1.5M, €500K | 1500000, 500000 |
| Wage | €200K | 200000 |
| Duplicates | Present | Removed |
| Special Characters | Present | Removed |
| Null Values | Inconsistent | Handled |

## Potential Use Cases

After cleaning, this dataset can be used for:
- Player performance analysis
- Market value predictions
- Club statistics and comparisons
- Player attribute correlations
- Machine learning model training
- Data visualization and dashboards

## Notes

- The conversion factors used are standard metric conversions
- All monetary values are in Euros (original currency)
- The cleaning process is reproducible and well-documented
- Edge cases and null values are handled appropriately

## Future Enhancements

- Add data validation checks
- Implement automated testing
- Create data quality reports
- Add more sophisticated outlier detection
- Implement logging for tracking changes


## Acknowledgments

- Dataset source: Kaggle 
- Built using pandas library

---
