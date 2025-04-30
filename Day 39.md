# Day 39 - 10 April 2025

1) Uploading the CSV File to Your Project Folder
    -Customers1.csv 
    -Make sure the path is correct for our environment  
2) Reading the File with Optimization
3) Practicing Optimization Techniques
4) Asking Chartgpt to how to save the optimized csv file 
    -Logged into [ChatGPT](https://openai.com/index/chatgpt/)
     ```
     How to save the optimized file
     ```
5) Converting object Columns to category
6) Converting Potential Date Columns



#Exercises

***Writing down dependencies***
```python
# /// script
# requires-python = ">=3.11"
# dependencies = [
#   "matplotlib",
#   "numpy",
#   "pandas"
# ]
# ///
```

***Optimized Pandas***
```python
import pandas as pd
import numpy as np
```

***Efficient Data Loading with optimized dtypes***
```python
dtype_dict = {
    "longitude": "float32",
    "latitude": "float32",
    "housing_median_age": "int16",
    "total_rooms": "int32",
    "total_bedrooms": "int32",
    "population": "int32",
    "households": "int32",
    "median_income": "float32",
    "median_house_value": "int32",
}
```

```python
import_path="customers1.csv"
df=pd.read_csv(import_path)
```

```python
initial_memory = df.memory_usage(deep=True).sum() / 1024**2 
print(f"Initial memory usage: {initial_memory:.2f} MB")
```

```python
for col in df.select_dtypes(include=['int64', 'float64']).columns:
    df[col] = pd.to_numeric(df[col], downcast='unsigned' if 'int' in str(df[col].dtype) else 'float')
```

```python
for col in df.select_dtypes(include='object').columns:
    num_unique_values = df[col].nunique()
    num_total_values = len(df[col])
    if num_total_values > 0 and (num_unique_values / num_total_values) < 0.5:
        df[col] = df[col].astype('category')
```

```python
for col in df.columns:
    if 'date' in col.lower():
        try:
            df[col] = pd.to_datetime(df[col], errors='coerce')
        except:
            pass
```

***Check memory usage***
```python
optimized_memory = df.memory_usage(deep=True).sum() / 1024**2
print(f"Optimized memory usage: {optimized_memory:.2f} MB")

reduction = initial_memory - optimized_memory
print(f"Memory reduced by: {reduction:.2f} MB ({(reduction / initial_memory) * 100:.1f}%)")

output_file = "customers1_optimized.csv"
df.to_csv(output_file, index=False)
print(f"\u2705 Optimized file saved as '{output_file}'")
```