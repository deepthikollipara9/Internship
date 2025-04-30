# Day 32 - 26 March 2025

1) Used chatgpt to understand few unknown topic in pandas
     - Upload the question you have doughts in
    ```
        pandas optimization techniques and best practices
    ```

#Excises

***Efficient Data Loading***
```python
dtype_dict = {'col1': 'int32', 'col2': 'float32', 'col3': 'category'}
df = pd.read_csv('data.csv', dtype=dtype_dict)
```

***Read Only Required Columns and Rows***
```python
df = pd.read_csv('data.csv', usecols=['col1', 'col2'], nrows=100000)
```

***Chunksize for large datasets***
```python
for chunk in pd.read_csv('data.csv', chunksize=50000):
    process(chunk)
```

***Convert Object Columns to Category***
```python
df['col'] = df['col'].astype('category')
```

***Downcast Numerical Columns***
```python
df['int_col'] = pd.to_numeric(df['int_col'], downcast='integer')
df['float_col'] = pd.to_numeric(df['float_col'], downcast='float')
```

***Vectorized Operations over Loops***
```python
df['new_col'] = df.eval("col1 + col2")
```

***Use apply() Sparingly***
```python
df['new_col'] = df['col'] * 2
```

***Efficient Filtering and Boolean Indexing***
```python
df = df.query("col > 10")
```

***Optimized Merging and Grouping***
```python
df.groupby('col')['value'].sum()
```

***Use Multi-threading with Modin***
```python
import modin.pandas as pd
df = pd.read_csv("large_data.csv")
```

***Use numba for JIT Compilation***
```python
from numba import jit

@jit(nopython=True)
def fast_func(arr):
    return arr * 2

df['new_col'] = fast_func(df['col'].values)
```

***Store Data in Efficient Formats***
```python
df.to_parquet("data.parquet", engine='fastparquet', compression='snappy')
df.to_feather("data.feather")
```

***Use eval() and query() for Faster Computations***
```python
df['new_col'] = df.eval("col1 + col2")
```

***Profile and Debug Performance***
```python
df.info(memory_usage='deep')
df.memory_usage(deep=True).sum() / 1e6
%timeit df['col'].sum()
import cProfile
cProfile.run("df.groupby('col').sum()")
```