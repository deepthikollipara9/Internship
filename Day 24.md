# Day 24 - 11 March 2025

1) Navigated to the desired folder on my system where I wanted to start a new project, and opened the terminal inside that folder.
2) Launched Visual Studio Code (VS Code) to set up my development environment quickly and efficiently.
3) Created a new Python file (like main.py) inside the project folder to start writing and testing code.
4) Practiced writing and running sample Python code to become more familiar with how uv handles virtual environments, package management, and general workflow inside VS Code.
5) Also went through some [YouTube videos](https://www.youtube.com/watch?v=KVoaIHAoiik) 


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

***Importing the packages***
```python
import pandas as pd
import numpy as np
```

***Writing the series***
```python
fru={'apples':30,'bananas':21}
fruits=pd.Series(fru)
print(fruits)
```

```python
fru={'apples':(35,41),'bananas':(21,34)}
fruits=pd.DataFrame.from_dict(fru,orient='index',columns=['2017 sales','2018 sales'])
print(fruits)
```

```python
ind={'flour':'4 cups','milk':'1 cup','eggs':'2 large','spam':'1 can'}
grocery=pd.Series(ind)
print(grocery)
```

```python
ani={'cow':[20,12],'goats':[22,19]}
animals=pd.DataFrame.from_dict(ani,orient='index',columns=['year 1','year 2'])
print(animals)
```

```python
dates=pd.date_range(start='05-01-2021',end='05-12-2021')
print(dates)
```

```python
date=pd.date_range(start='05-01-2021',end='05-12-2021')
df=pd.DataFrame(np.random.randn(12,4),index= date ,columns=list('ABCD'))
print(df)
```

```python
df2=pd.DataFrame({'a':1.0,
                  'b':pd.Timestamp('20130102'),
                  'c':pd.Series(1,index=list(range(4)),dtype='float32'),
                  'd':pd.Categorical(['test','train','test','train']),
                  'e':'foo',
                  'f':np.array([3]*4,dtype='int32')})
print(df2)
```

```python
print(df2.dtypes)
```

```python
print(df2.head())
```

```python
print(df2.tail(2))
```

```python
print(df2.index)
```

```python
print(df2.columns)
```

```python
print(df2.to_numpy())
```

```python
print(df2.describe())
```

```python
print(df.transpose)
```

```python
print(df.sort_index(axis=1,ascending=False))
```

```python
print(df2.sort_values(by='d'))
```

```python
print(df['A'])
```

```python
print(df[0:3])
```

```python
print(df.loc[dates[0]])
```

```python
print(df2.iloc[2])
```

```python
print(df2.iloc[3:5,0:2])
```

```python
print(df2.iloc[1,1])
```

```python
print(df[df['A']>0])
```

```python
s1=pd.Series ([1,2,3,4,5,6],index=pd.date_range('20130102',periods=6))
print(s1)
```

```python
a=df.at[dates[0],'A']
print(a)
```

```python
df2=df.copy()
df2[df2>0]=-df2
print(df2)
```

```python
print(df)
```

```python
print(df.dropna(how='any'))
```

```python
print(df.fillna(value=5))
```

```python
a=pd.isna(df)
print(a)
```

```python
print(df.mean())
```

***Running the code file***
```bash
uv run pythoncode.py
```