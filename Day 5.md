# Day 5- 10 Feb 2025

1) Exporing more pandas function  from  official [site](https://pandas.pydata.org/docs/user_guide/10min.html#min)
2) Used chatgpt to understand few unknown topic in pandas
     - Upload the question you have doughts in
    ```
        Explain the above question in detail
    ```

# Exercise

***Display the date range of 12 days***

```python
from datetime import datetime
import pandas as pd
import numpy as np
date=pd.date_range(start='05-01-2021',end='05-12-2021')
df=pd.DataFrame(np.random.randn(12,4),index=date,columns=list('ABCD'))
print(df)
```

***where the index is the date***

```python
print(df.mean(axis=1))
```

***How does shift work***

```python
import pandas as pd
import numpy as np
date=pd.date_range(start='05-01-2021',end='05-12-2021')
s=pd.Series([1,3,5,np.nan,6,8,0,0,0,0,0,0],index=date).shift(2)
print(s)
```

***How does indexing work***

```python
a=df.sub(s,axis='index')
print(a)
```

***How does lambda work***

```python
b=df.agg(lambda x:np.mean(x)*5.6)
print(b)
```

***How does transform lambda work***

```python
c=df.transform(lambda x:x*101.2)
print(c)
```

***Display randam series***

```python
import pandas as pd
import numpy as np
s1=pd.Series(np.random.randint(0,7,size=10))
print(s1)
```

***Display values in series***

```python
d=s1.value_counts()
print(d)
```

***Display series values in lower case***

```python
import pandas as pd
import numpy as np
s3=pd.Series(['A','B','C','D','AaBcD','BaCD',np.nan,'CABA','dog','cat'])
e=s3.str.lower()
print(e)
```

***Display series in randam values***

```python
df=pd.DataFrame(np.random.randn(10,4))
print(df)
```

***Display series in values***

```python
left=pd.DataFrame({'key':['foo','foo'],'lval':[1,2]})
right=pd.DataFrame({'key':['foo','foo'],'rval':[4,5]})
print(left)
print(right)
```

***Merging series values***

```python
f=pd.merge(left,right,on='key')
print(f)
```

***Displaying an other dataframe***

```python
import pandas as pd
import numpy as np
df2=pd.DataFrame({'A':['foo','bar','foo','bar','foo','bar','foo','foo'],
                  'B':['one','one','two','three','two','two','one','three'],
                  'C':np.random.randn(8),
                  'D':np.random.randn(8)})
print(df2)
```

***Displaying  grouping data***

```python
g=df2.groupby('A')[['C','D']].sum()
print(g)
```

***Displaying  grouping data***

```python
h=df2.groupby(['A','B']).sum()
print(h)
```

***Displaying  grouping data using arrays***

```python
arrays=[['bar','bar','baz','baz','foo','foo','qux','qux'],
        ['one','two','one','two','one','two','one','two']]
index=pd.MultiIndex.from_arrays(arrays,names=['first','second'])
df3=pd.DataFrame(np.random.randn(8,2),index=index,columns=['A','B'])
df4=df3[:4]
print(df4)
print(df3)
```

***Displaying  stacked functions***

```python
stacked=df4.stack(future_stack=True)
print(stacked)
```

```python
print(stacked.unstack())
```

```python
print(stacked.unstack(1))
```

```python
print(stacked.unstack(0))
```

***Displaying  other dataframe***

```python
df=pd.DataFrame({'A':['one','one','two','three']*3,
                 'B':['A','B','C']*4,
                 'C':['foo','foo','foo','bar','bar','bar']*2,
                 'D':np.random.randn(12),
                 'E':np.random.randn(12)})
print(df)
```

***Displaying  pivot table***

```python
i=pd.pivot_table(df,values='D',index=['A','B'],columns=['C'])
print(i)
```

***Displaying  dict function***

```python
import pandas as pd
dict={'name':['rom','ram','sam','cham'],
      'degree':['mtech','btech','mba','bca'],
      'score':[80,82,96,92]}
df=pd.DataFrame(dict)
for(i,j) in df.iterrows():
    print(i,j)
    print()
```
