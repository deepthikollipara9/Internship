# Day 4- 07 Feb 2025

1) Exporing more pandas function  from the kaggle official [site](https://www.kaggle.com/learn/pandas)
    - login to [Kaggle](https://www.kaggle.com/account/login?phase=startSignInTab&returnUrl=%2F)
2) Practing few data frame programs from [exercises](https://www.kaggle.com/code/scratchpad/notebookea620051cc/edit)


# Execises

***Print fruits data in form of database***

```python
import pandas as pd
fru={'apples':30,'bananas':21}
fruits=pd.Series(fru)
print(fruits)
```

***Adding index values***

```python
import pandas as pd
fru={'apples':(35,41),'bananas':(21,34)}
fruits=pd.DataFrame.from_dict(fru,orient='index',columns=['2017 sales','2018 sales'])
print(fruits)
```

***Creating the ingredients needed***

```python
import pandas as pd
ind={'flour':'4 cups','milk':'1 cup','eggs':'2 large','spam':'1 can'}
grocery=pd.Series(ind)
print(grocery)
```

***Creating the dataframe for animals***

```python
import pandas as pd
ani={'cow':[20,12],'goats':[22,19]}
animals=pd.DataFrame.from_dict(ani,orient='index',columns=['year 1','year 2'])
print(animals)
```

***Display the dates***

```python
import pandas as pd
dates=pd.date_range(start='05-01-2021',end='05-12-2021')
print(dates)
```

***Display the dates with index***

```python
from datetime import date
import pandas as pd
import numpy as np
date=pd.date_range(start='05-01-2021',end='05-12-2021')
df=pd.DataFrame(np.random.randn(12,4),index= date ,columns=list('ABCD'))
print(df)
```

***Displaying timestamp***

```python
import pandas as pd
import numpy as np

df2=pd.DataFrame({'a':1.0,
                  'b':pd.Timestamp('20130102'),
                  'c':pd.Series(1,index=list(range(4)),dtype='float32'),
                  'd':pd.Categorical(['test','train','test','train']),
                  'e':'foo',
                  'f':np.array([3]*4,dtype='int32')})
print(df2)
```

***Displaying datatype of frame***

```python
print(df2.dtypes)
```

***Display data***

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
