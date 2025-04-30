# Day 35 - 1 April 2025

1) Reducing Memory Usage with Data Types
    -Convert float64 to float32, int64 to int32, and object to category when possible.
    -Use df.info(memory_usage='deep') to see true memory usage.
    -[Pandas Data Types Optimization](https://pythonspeed.com/articles/pandas-large-datasets/)
2) Efficient File Reading
    -Use pd.read_csv(..., chunksize=...) to process large CSVs in chunks.
    -Use usecols and dtype during reading to load only what’s needed.
    -[Efficient Reading](https://pandas.pydata.org/docs/reference/api/pandas.read_csv.html) with read_csv
3) Vectorized Operations
    -Avoid loops or .apply() if possible — use vectorized NumPy operations for speed.
    -Example: df['new_col'] = df['a'] + df['b'] instead of using .apply().
    -[Vectorization in Pandas](https://realpython.com/pandas-python-explore-dataset/#speeding-things-up-with-vectorization)
4) Use .query() and .eval()
    -Faster alternatives to traditional filtering and computation.
    -Example: df.query('col1 > 100') is quicker than df[df['col1'] > 100].
    -[Pandas eval and query documentation](https://pandas.pydata.org/docs/user_guide/enhancingperf.html#enhancingperf-eval)
5) Categorical Data
    -Convert object columns with repetitive values (like city names) to category type.
    -Reduces memory and improves performance in groupby/filtering.
    -[Categoricals in Pandas](https://pandas.pydata.org/docs/user_guide/categorical.html)
6) Avoid Copying Large DataFrames
    -Use inplace=True for functions like .drop(), .fillna(), etc. to avoid unnecessary memory usage.
    -Or chain efficiently: df.drop('col', axis=1).reset_index(drop=True)
7) Use Profiling Tools
    -Use pandas_profiling, memory_profiler, or line_profiler for deeper insights.
    -[Pandas Profiling on GitHub](https://github.com/ydataai/ydata-profiling)
8) Use NumPy Wherever Possible
    -NumPy operations are generally faster than Pandas for numerical work.
    -[NumPy and Performance](https://numpy.org/doc/stable/user/absolute_beginners.html)