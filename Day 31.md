# Day 31 - 24 March 2025

1) Used chatgpt to understand few unknown topic in pandas
     - Upload the question you have doughts in
    ```
        pandas optimization techniques and best practices
    ```
2) Exploring the Optimization of Pandas
   -Learned how to optimize memory usage using astype() to convert data types
   -Used df.info(memory_usage='deep') to check detailed memory consumption.
   -Handled large datasets by reading in chunks using pd.read_csv(..., chunksize=10000).
   -Replaced apply() with vectorized operations whenever possible for faster performance.
   -Used query() and eval() for faster filtering and computation on DataFrames.
   -Avoided unnecessary loops by using built-in pandas functions for aggregation, merging, and reshaping.
   -Explored performance profiling using %timeit in Jupyter to compare performance between different approaches. 
3) Understanding More About Pandas Functions
   -Revisited core functions like groupby(), merge(), pivot_table(), and melt() for data wrangling.
   -Practiced with fillna(), dropna(), and isnull() for cleaning and handling missing data.
   -Learned about applymap() vs map() vs apply() for row-wise or element-wise transformations.
   -Created new columns with conditional logic using np.where() or df.loc[].
   -Practiced with string operations using str.contains(), str.replace(), str.extract() for text data.
   -Used resample() for working with time series data and aggregation over time intervals.
   -Explored pd.to_datetime() and dt accessor to manipulate date/time fields.

