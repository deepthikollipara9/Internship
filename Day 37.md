# Day 37 - 8 April 2025

1) Uploading the CSV File to Your Project Folder
    -Housing.csv 
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
def load_data(file_path):
    return pd.read_csv(file_path, dtype=dtype_dict)

df = load_data("housing.csv")
```

```python
def downcast_numeric(df):
    for col in df.select_dtypes(include=["float", "int"]):
        df[col] = pd.to_numeric(df[col], downcast="integer")
    return df

df = downcast_numeric(df)

print("Script is running...")
print(df.head())
```

***Vectorized Operations instead of loops***
```python
df["rooms_per_household"] = df["total_rooms"] / df["households"]
df["bedrooms_per_room"] = df["total_bedrooms"] / df["total_rooms"]
df["population_per_household"] = df["population"] / df["households"]
```

***Efficient Filtering using .query()***
```python
df_filtered = df.query("median_house_value > 200000 and median_income > 5")
```

***Optimized Grouping***
```python
df_grouped = df.groupby("housing_median_age")["median_house_value"].mean()

print(df_filtered.head())  
print(df_grouped.head())

df.eval("room_per_household = total_rooms / households", inplace=True)
df.eval("people_per_house = population / households", inplace=True)

print("Room per Household:\n", df["room_per_household"].head())
print("People per House:\n", df["people_per_house"].head())

df_filtered = df.query("median_income > 6 and median_house_value > 250000")

print("Filtered Data (median_income > 6 and median_house_value > 250000):\n")
print(df_filtered.head())
```

***Check memory usage***
```python
mem = df.memory_usage(deep=True).sum() / 1024**2
print(f"Total memory used: {mem:.2f} MB")

print(df.info(memory_usage='deep')) 
print(df.head())

df_optimized = df.astype('float32')

optimized_memory = df_optimized.memory_usage(deep=True).sum() / 1024**2 
print(f"Optimized memory usage: {optimized_memory:.2f} MB")
```