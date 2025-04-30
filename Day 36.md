# Day 36 - 7 April 2025

1) Referring to a Few Optimization Techniques from Official and Community Websites
    -[Pandas Enhancing Performance](https://pandas.pydata.org/docs/user_guide/enhancingperf.html)
    -[PythonSpeed - Pandas with Large Datasets](https://pythonspeed.com/articles/pandas-large-datasets/)
2) Asked ChatGPT to Provide Sample Questions Related to Pandas Optimization
    -Logged into [ChatGPT](https://openai.com/index/chatgpt/)
    ```
      give me sample question
      ```


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

***Load data efficiently with types and selected columns***
```python
df = pd.read_csv("data.csv", dtype={"id": "int32", "gender": "category"}, usecols=["id", "name", "gender", "age"])
```

***Filter rows with query***
```python
df_filtered = df.query("age > 30")
```

***Add new column with vectorized calculation***
```python
df["bonus"] = df["salary"] * 0.10
```

***Combine string columns efficiently***
```python
df["full_name"] = df["first_name"].str.cat(df["last_name"], sep=" ")
```

***Group and aggregate efficiently***
```python
department_avg_salary = df.groupby("department")["salary"].mean()
```

***Downcast numeric columns to save memory***
```python
df["age"] = pd.to_numeric(df["age"], downcast="integer")
df["score"] = pd.to_numeric(df["score"], downcast="float")
```

***Convert object to category for repeated strings***
```python
df["gender"] = df["gender"].astype("category")
```

***Conditional assignment with np.where***
```python
df["status"] = np.where(df["age"] > 60, "senior", "adult")
```

***Drop nulls from specific important columns***
```python
df.dropna(subset=["email", "phone"], inplace=True)
```

***Save in efficient format***
```python
df.to_parquet("data.parquet", compression="snappy")
```

***Optimized merge with indexing***
```python
df1.set_index("id", inplace=True)
df2.set_index("id", inplace=True)
df_combined = df1.join(df2, how="inner")
```

***Evaluate expression using eval***
```python
df.eval("adjusted_salary = salary * 1.1 + bonus", inplace=True)
```

***Check memory usage***
```python
df.info(memory_usage="deep")
print("Total memory usage (MB):", df.memory_usage(deep=True).sum() / 1024**2)
```