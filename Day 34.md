# Day 34 - 31 March 2025

1) Discovered how indexing can speed up data selection and slicing.
2) Created custom indices using df.set_index() and understood when to reset with df.reset_index().
3) Learned the impact of inplace operations on memory efficiency.
4) Used inplace=True carefully to avoid unnecessary memory copying.
5) Tested performance differences using %timeit and %%timeit in Jupyter Notebooks.
6) Compared traditional loops with vectorized Pandas code for timing.
7) Explored using .loc[] and .iloc[] over direct indexing for better clarity and sometimes performance.
8) Filtered large datasets using boolean masking rather than .apply() or loops.
      ```python
         df[df['column'] > 100]
      ```
9) Applied categorical data types for repeated string/object values.
10) Used memory_usage(deep=True) to evaluate memory before and after type conversion.
11) Learned to drop unused columns early in the pipeline to save memory.
      ```python
         df.drop(['col1', 'col2'], axis=1, inplace=True)
      ```
12) Explored Dask and Modin as alternatives to Pandas for handling huge datasets with similar syntax.
13) Followed GitHub discussions and community forums for real-world optimization tips and tricks.
14) Watched advanced [YouTube](https://www.youtube.com/watch?v=HN5d490_KKk) videos focused on large-scale data performance in Pandas.