# Day 7 - 13 Feb 2025

1) Exporing how to add file to colab notebook from the [youtube](https://www.youtube.com/watch?v=ZjO-DFVdbeQ)
2) Learning how to write sql queries in colab notebook from the [youtube](https://www.youtube.com/watch?v=WaKOnXTKyhU)
3) uploading the database file in colab to run the queries
4) Generated sample questions using chatgpt
    - login to [ChatGPT](https://openai.com/index/chatgpt/)
    - Upload the database dump to chatgpt to analyze
    - Written the prompt to generate sample questions
        ```
        Generate few sqlite question the given database 
        ```
  5) Used chatgpt to understand few unknown topic in sql
     - Upload the question you have doughts in
      ```
         Explain the above question in detail
      ```
      

# Exercise

***Uploading file***

```python
from google.colab import files
uploaded=files.upload()
```

***Connecting the database with the cursor***

```python
import sqlite3
db_path="tips.db"
conn=sqlite3.connect(db_path)
cursor=conn.cursor()
cursor.execute("SELECT * FROM observation")
rows=cursor.fetchall()
for row in rows:
  print(row)
conn.close()
```

***Connecting the sql quries***

```python
import sqlite3
db_path='tips.db'
sql_file_path='1.sql'
conn=sqlite3.connect(db_path)
cursor=conn.cursor()
with open(sql_file_path,'r') as sql_file:
  sql_script=sql_file.read()
conn.commit()
conn.close()
print('sql script executed successfully!')
```

***Displaying the table with limit 5***

```python
import pandas as pd
conn=sqlite3.connect(db_path)
query='SELECT * FROM Observation LIMIT 5;'
df=pd.read_sql_query(query,conn)
conn.close()
print(df)
```

***Displaying the table with limit 15***

```python
import pandas as pd
conn=sqlite3.connect(db_path)
query='SELECT * FROM Observation LIMIT 15;'
df=pd.read_sql_query(query,conn)
conn.close()
print(df)
```

***Displaying bills where tips are more than 2***

```python
import pandas as pd
import sqlite3
db_path='tips.db'
conn=sqlite3.connect(db_path)
query='SELECT * FROM Observation WHERE tip>2;'
df=pd.read_sql_query(query,conn)
print(df)
conn.close()
```

***Displaying gender of the customers***

```python
import pandas as pd
import sqlite3
db_path='tips.db'
conn=sqlite3.connect(db_path)
query='SELECT * FROM Sex;'
df=pd.read_sql_query(query,conn)
print(df)
conn.close()
```

***Displaying total bill of male customer whoes tips are more than 2***

```python
import pandas as pd
import sqlite3
db_path='tips.db'
conn=sqlite3.connect(db_path)
query='SELECT * FROM Observation WHERE sex_id=1 AND tip>2;'
df=pd.read_sql_query(query,conn)
print(df)
conn.close()
```

***Displaying total revenue***

```python
import pandas as pd
import sqlite3
db_path='tips.db'
conn=sqlite3.connect(db_path)
query='SELECT sum(total_bill) FROM Observation AS total_revenue;'
df=pd.read_sql_query(query,conn)
print(df)
conn.close()
```

***Displaying total revenue earned only by male customer bill***

```python
import pandas as pd
import sqlite3
db_path='tips.db'
conn  =sqlite3.connect(db_path)
query='SELECT sum(total_bill) FROM Observation WHERE sex_id=1;'
df=pd.read_sql_query(query,conn)
print(df)
conn.close()
```

***Count of observation***

```python
import pandas as pd
import sqlite3
db_path='tips.db'
conn=sqlite3.connect(db_path)
query='select count(*) from Observation;'
df=pd.read_sql_query(query,conn)
print(df)
conn.close()
```
