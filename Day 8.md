# Day 8 - 14 Feb 2025

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
db_path='tips.db'
conn=sqlite3.connect(db_path)
cursor=conn.cursor()
conn.close()
```

***Displaying the table***

```python
import pandas as pd
import sqlite3
db_path='tips.db'
conn=sqlite3.connect(db_path)
df=pd.read_sql_query('SELECT * FROM observation',conn)
print(df)
conn.close()
```

***Displaying the bill of male customers***

```python
import pandas as pd
import sqlite3
db_path='tips.db'
conn=sqlite3.connect(db_path)
df=pd.read_sql_query('SELECT * FROM observation WHERE sex_id=0',conn)
print(df)
conn.close()
```

***Total bill of male smokers***

```python
import pandas as pd
import sqlite3
db_path='tips.db'
conn=sqlite3.connect(db_path)
df=pd.read_sql_query('SELECT * FROM observation WHERE sex_id=0 AND smoker_id=1',conn)
print(df)
conn.close()
```

***Total bill by male customers in thursday night***

```python
import pandas as pd
import sqlite3
db_path='tips.db'
conn=sqlite3.connect(db_path)
df=pd.read_sql_query('SELECT * FROM observation WHERE sex_id=0 AND day_id=0',conn)
print(df)
```

***Male customer bills is more that $10***

```python
import pandas as pd
import sqlite3
db_path='tips.db'
conn=sqlite3.connect(db_path)
df=pd.read_sql_query('SELECT * FROM observation WHERE sex_id=0 and total_bill>10',conn)
print(df)
conn.close()
```

***Female customer bill is more than $10 and tip is more than 5***

```python
import pandas as pd
import sqlite3
db_path='tips.db'
conn=sqlite3.connect(db_path)
df=pd.read_sql_query('SELECT * FROM observation WHERE sex_id=1 and total_bill>10 AND tip>5',conn)
print(df)
conn.close()
```

***Total bill by female non smokers***

```python
import pandas as pd
import sqlite3
db_path='tips.db'
conn=sqlite3.connect(db_path)
df=pd.read_sql_query('SELECT * FROM observation WHERE sex_id=1 AND smoker_id=1 ',conn)
print(df)
```

***Displaying total bill female non smokers on saturday***

```python
import pandas as pd
import sqlite3
db_path='tips.db'
conn=sqlite3.connect(db_path)
df=pd.read_sql_query('SELECT * FROM observation WHERE sex_id=1 AND smoker_id=1  AND day_id=3',conn)
print(df)
conn.close()
```

***Total bill of female non smokers on Saturday lunch time***

```python
import pandas as pd
import sqlite3
db_path='tips.db'
conn=sqlite3.connect(db_path)
df=pd.read_sql_query('SELECT * FROM observation WHERE sex_id=1 AND smoker_id=1  AND day_id=3 AND time_id=1',conn)
print(df)
conn.close()
```

***Total bill of party size is 4***

```python
import pandas as pd
import sqlite3
db_path='tips.db'
conn=sqlite3.connect(db_path)
df=pd.read_sql_query('SELECT * FROM observation WHERE size=4',conn)
print(df)
conn.close()
```

***Total bill of male customers party size is 4***

```python
import pandas as pd
import sqlite3
db_path='tips.db'
conn=sqlite3.connect(db_path)
df=pd.read_sql_query('SELECT * FROM observation WHERE size=4 AND sex_id=0',conn)
print(df)
conn.close()
```

***Total bill of male smokers party size is 4***

```python
import pandas as pd
import sqlite3
db_path='tips.db'
conn=sqlite3.connect(db_path)
df=pd.read_sql_query('SELECT * FROM observation WHERE size=4 AND sex_id=0 AND smoker_id=1',conn)
print(df)
```

***Total bill of male non smokers party size is 4***

```python
import pandas as pd
import sqlite3
db_path='tips.db'
conn=sqlite3.connect(db_path)
df=pd.read_sql_query('SELECT * FROM observation WHERE size=4 AND sex_id=0 AND smoker_id=1 AND day_id=0',conn)
print(df)
conn.close()
```

***Total bill of smokers party size is 3***

```python
import pandas as pd
import sqlite3
db_path='tips.db'
conn=sqlite3.connect(db_path)
df=pd.read_sql_query('SELECT * FROM observation WHERE size=3 AND smoker_id=0',conn)
print(df)
```

***Total bill of smokers party size is 3 on friday***

```python
import pandas as pd
import sqlite3
db_path='tips.db'
conn=sqlite3.connect(db_path)
df=pd.read_sql_query('SELECT * FROM observation WHERE size=3 AND smoker_id=0 AND day_id=2',conn)
print(df)
conn.close()
```

***Total bill is greater than $10***

```python
import pandas as pd
import sqlite3
db_path='tips.db'
conn=sqlite3.connect(db_path)
df=pd.read_sql_query('SELECT * FROM observation WHERE total_bill>10',conn)
print(df)
conn.close()
```

***Total bill is greater than $10 and tip is grater than $5***

```python
import pandas as pd
import sqlite3
db_path='tips.db'
conn=sqlite3.connect(db_path)
df=pd.read_sql_query('SELECT * FROM observation WHERE total_bill>10 AND tip>5',conn)
print(df)
conn.close()
```

***Total bill of male customer is greater than $10 and tip is grater than $5***

```python
import pandas as pd
import sqlite3
db_path='tips.db'
conn=sqlite3.connect(db_path)
df=pd.read_sql_query('SELECT * FROM observation WHERE total_bill>10 AND tip>5 AND sex_id=0',conn)
print(df)
conn.close()
```

***Total bill of female customer is greater than $10 and tip is grater than $5***

```python
import pandas as pd
import sqlite3
db_path='tips.db'
conn=sqlite3.connect(db_path)
df=pd.read_sql_query('SELECT * FROM observation WHERE total_bill>10 AND tip>5 AND sex_id=1',conn)
print(df)
conn.close()
```

***Total bill of smokers customer who tip is grater than $5***

```python
import pandas as pd
import sqlite3
db_path='tips.db'
conn=sqlite3.connect(db_path)
df=pd.read_sql_query('SELECT * FROM observation WHERE  tip>5  AND smoker_id=1',conn)
print(df)
conn.close()
```

***Total bill of smokers customer who tip is grater than $5 on thursday***

```python
import pandas as pd
import sqlite3
db_path='tips.db'
conn=sqlite3.connect(db_path)
df=pd.read_sql_query('SELECT * FROM observation WHERE  tip>5  AND smoker_id=1 AND day_id=0',conn)
print(df)
```

***Total bill of smokers customer on Thursday lunch***

```python
conn=sqlite3.connect(db_path)
df=pd.read_sql_query('SELECT * FROM observation WHERE smoker_id=1 AND day_id=0 AND time_id=0',conn)
print(df)
```

***Total bill of smokers customer on Sunday where bill is more than $10***

```python
conn=sqlite3.connect(db_path)
df=pd.read_sql_query('SELECT * FROM observation WHERE smoker_id=1 AND day_id=3 AND total_bill>10',conn)
print(df)
```

***Total bill of customer on Sunday where bill is more than $10 and tip is more than $5***

```python
conn=sqlite3.connect(db_path)
df=pd.read_sql_query('SELECT * FROM observation WHERE day_id=3 AND total_bill>10 AND tip>5',conn)
print(df)
```

***Total bill of  male customer on Sunday where bill is more than $10 and tip is more than $5***

```python
df=pd.read_sql_query('SELECT * FROM observation WHERE day_id=3 AND total_bill>10 AND tip>5 AND sex_id=0',conn)
print(df)
```

***Total average of tip***

```python
query='select avg(tip) from observation;'
df=pd.read_sql_query(query,conn)
print(df)
```

***Total average of tip per day***

```python
query='select day.day,avg(observation.tip) as avg_tip from observation join day on observation.day_id=day.day_id group by day.day;'
df=pd.read_sql_query(query,conn)
print(df)
```

***Smoker tips are more or non smoker***

```python
query='select smoker.smoker,avg(observation.tip) as avg_tip from observation join smoker on observation.smoker_id=smoker.smoker_id group by smoker.smoker;'
df=pd.read_sql_query(query,conn)
print(df)
```

***Diff in tips between male and female***

```python
query='select sex.sex,avg(observation.tip) as avg_tip from observation join sex on observation.sex_id=sex.sex_id group by sex.sex;'
df=pd.read_sql_query(query,conn)
print(df)
```

***More tips in lunch or dinner***

```python
query='select time.time,avg(observation.tip) as avg_tip from observation join time on observation.time_id=time.time_id group by time.time;'
df=pd.read_sql_query(query,conn)
print(df)
```

***Day of week with highest tip***

```python
query='select day.day,avg(observation.tip) as avg_tip from observation join day on observation.day_id=day.day_id group by day.day;'
df=pd.read_sql_query(query,conn)
print(df)
```

***Largest bill***

```python
query='select total_bill,avg(tip) as avg_tip from observation group by total_bill limit 5;'
df=pd.read_sql_query(query,conn)
print(df)
```

***Lowest bill***

```python
query='select total_bill,avg(tip) as avg_tip from observation group by total_bill limit 1;'
df=pd.read_sql_query(query,conn)
print(df)
```

***Detemine 10 smokers***

```python
query='select * from observation where smoker_id=1 limit 10;'
df=pd.read_sql_query(query,conn)
print(df)
```

***Where total more than 20 and tip is more than 5 both***

```python
query='select * from observation where total_bill>20 and tip>5;'
df=pd.read_sql_query(query,conn)
print(df)
```

***Write a query to categorize customer based on tip amount***

```python
query='select tip, case when tip>5 then "High" when tip between 3 and 5 then "Medium" else "Low" end as tip_category from observation;'
df=pd.read_sql_query(query,conn)
print(df)
```

***Write a query to display weekend for saturday and sunday and weekday for rest***

```python
query='select day, case when day in ("Saturday","Sunday") then "Weekend" else "Weekday" end as day_category from day;'
df=pd.read_sql_query(query,conn)
print(df)
```

***Round the average tip amount to 2 decimal places***

```python
query='select round(avg(tip),2) as avg_tip from observation;'
df=pd.read_sql_query(query,conn)
print(df)
```

***Find the total revenue generated per day***

```python
query='select sum(total_bill) as total_revenue from observation '
df=pd.read_sql_query(query,conn)
print(df)
```

***Write a query to find the total number of records in the observation table***

```python
query='select count(*) as total_records from observation;'
df=pd.read_sql_query(query,conn)
print(df)
```