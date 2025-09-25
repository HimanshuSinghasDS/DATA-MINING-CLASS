# Data Cleaning Assignment - Wine Dataset

**Course:** Data Fundamentals / Python Programming  
**Instructor:** Himanshu Singh  
**Institution:** SSCBS, University of Delhi

## Assignment Overview

You are provided with a "dirty" wine dataset (`wine_dataset_dirty_for_students.csv`) that contains various data quality issues. Your task is to clean this dataset using Python and prepare it for machine learning analysis.

## Dataset Information

- **Source:** Wine Recognition Dataset (UCI Machine Learning Repository)
- **Rows:** 185 (including problematic entries)  
- **Columns:** 14 (13 features + 1 target variable)
- **Target Variable:** Wine class (0, 1, 2)

### Features:
- `alcohol`: Alcohol percentage in wine
- `malic_acid`: Malic acid content  
- `ash`: Ash content
- `alcalinity_of_ash`: Alkalinity of ash
- `magnesium`: Magnesium content (mg)
- `total_phenols`: Total phenolic compounds
- `flavanoids`: Flavanoid content
- `nonflavanoid_phenols`: Non-flavanoid phenolic compounds
- `proanthocyanins`: Proanthocyanin content
- `color_intensity`: Color intensity
- `hue`: Hue value
- `od280/od315_of_diluted_wines`: OD280/OD315 ratio
- `proline`: Proline content (mg/L)

## Known Data Quality Issues

The dataset contains the following issues that you need to address:

1. **Missing Values** (~36 missing values across multiple columns)
2. **Duplicate Rows** (~5-7 duplicate entries)
3. **Outliers** (extreme values that don't make sense chemically)
4. **Inconsistent Values** (negative values where they shouldn't exist)
5. **Data Type Issues** (mixed data types in some columns)
6. **Invalid Target Values** (target values outside expected range 0-2)

## Your Tasks

### Task 1: Data Exploration and Assessment (20 points)

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Load the dataset
df = pd.read_csv('wine_dataset_dirty_for_students.csv')

# Your code here:
# 1. Display basic information about the dataset
# 2. Check for missing values
# 3. Identify data types
# 4. Check for duplicates
# 5. Display basic statistics
```

### Task 2: Define Validation Rules (20 points)

Create a validation framework with realistic ranges for each feature:

```python
def define_validation_rules():
    """
    Define validation rules for wine dataset features.
    Research typical ranges for wine chemical properties.
    """
    rules = {
        # Example:
        'alcohol': {
            'min': 8.0,    # Minimum alcohol content for wine
            'max': 20.0,   # Maximum realistic alcohol content  
            'type': float,
            'required': True
        },
        # Add rules for other columns...
    }
    return rules

# Implement a function to check violations
def validate_data(df, rules):
    """Apply validation rules and report violations"""
    # Your implementation here
    pass
```

### Task 3: Handle Missing Values (20 points)

```python
# Implement missing value handling strategies
# Consider different approaches:
# - Mean/Median imputation for numerical data
# - Mode imputation for categorical data
# - Domain-specific imputation strategies

# Your code here:
```

### Task 4: Handle Duplicates (10 points)

```python
# Identify and remove duplicate rows
# Consider both exact duplicates and near-duplicates

# Your code here:
```

### Task 5: Handle Outliers (15 points)

```python
# Implement outlier detection and treatment
# Methods to consider:
# - IQR method
# - Z-score method
# - Domain knowledge-based bounds
# - Winsorizing vs. removal

# Your code here:
```

### Task 6: Fix Inconsistent Values (10 points)

```python
# Handle data type issues and inconsistent values
# - Convert mixed data types
# - Fix negative values where inappropriate
# - Standardize categorical values

# Your code here:
```

### Task 7: Final Validation and Report (5 points)

```python
# Generate a comprehensive cleaning report
# - Before vs. after comparison
# - Summary of actions taken
# - Final data quality assessment

# Your code here:
```

## Submission Requirements

Submit the following files:

1. **`student_name_data_cleaning.py`** - Your complete Python script
2. **`wine_dataset_cleaned.csv`** - Your cleaned dataset
3. **`cleaning_report.txt`** - A text report summarizing:
   - Issues identified
   - Cleaning actions taken
   - Final data quality metrics
   - Any assumptions made

## Evaluation Criteria

- **Code Quality (20%)**: Clean, well-commented, efficient code
- **Problem Identification (20%)**: Correctly identifying all data quality issues
- **Cleaning Techniques (40%)**: Appropriate use of cleaning methods
- **Validation (10%)**: Proper validation of cleaned data
- **Documentation (10%)**: Clear reporting and explanation of decisions

## Expected Outcomes

After cleaning, your dataset should:
- Have **zero missing values** (or justified strategic missingness)
- Have **no duplicate rows**
- Have **all values within realistic ranges**
- Have **consistent data types**
- Have **valid target values** (0, 1, 2 only)
- Be **ready for machine learning** analysis

## Hints and Tips

1. **Start with exploration** - understand your data before cleaning
2. **Document your decisions** - explain why you chose specific cleaning methods
3. **Validate continuously** - check your work at each step  
4. **Consider domain knowledge** - use wine chemistry knowledge to set realistic bounds
5. **Test your cleaning pipeline** - make sure it works on the entire dataset

## Bonus Challenges (Optional)

1. **Implement automated outlier detection** using multiple methods
2. **Create visualizations** showing before/after cleaning effects
3. **Build a reusable data cleaning pipeline** that could work on similar datasets
4. **Investigate correlations** between features to inform imputation strategies

## Resources

- Pandas Documentation: https://pandas.pydata.org/docs/
- Scikit-learn Preprocessing: https://scikit-learn.org/stable/modules/preprocessing.html
- Wine Chemistry References: Research typical ranges for wine chemical properties

## Submission Deadline

**Due Date:** [Insert your deadline here]  
**Submission Method:** [Insert your preferred submission method]

---

**Questions?** Contact: Himanshu Singh (himanshu.singh@sscbs.du.ac.in)

Good luck with your data cleaning assignment!