# Day 38 - 9 April 2025

1) Uploading the CSV File to Your Project Folder
    -Customers.csv 
    -Make sure the path is correct for our environment  
2) Reading the File with Optimization
3) Practicing Optimization Techniques


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
df=pd.read_csv("customers.csv")
```

```python
initial_memory = df.memory_usage(deep=True).sum() / 1024**2 
print(f"Initial memory usage: {initial_memory:.2f} MB")
```

```python
df['Index'] = pd.to_numeric(df['Index'], downcast='integer')
```

***Check memory usage***
```python
optimized_memory = df.memory_usage(deep=True).sum() / 1024**2
print(f"Optimized memory usage: {optimized_memory:.2f} MB")

reduction = initial_memory - optimized_memory
print(f"Memory reduced by: {reduction:.2f} MB ({(reduction / initial_memory) * 100:.1f}%)")
```