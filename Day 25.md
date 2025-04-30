# Day 25 - 12 March 2025

1) Upload the Database into the Project Folder
   -Place your database file (tips.db) into your project folder (e.g., myproject)
2) Navigate to the Project Folder and Open Terminal
   -Right-click inside the myproject folder.
   -Select "Open in Terminal" or "Open with Terminal" depending on your system.
3) Open Visual Studio Code from Terminal
   -In the terminal window
    ```bash
    code .
    ``` 
4) Verify Database File in VS Code
   -Inside Visual Studio Code, check the Explorer sidebar.
   -You should see your database file (.db, .sqlite, .csv, etc.) listed there.
5) Practice Connecting to the Database

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
import sqlite3
```

***Writing the quries***
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

```python
import pandas as pd
conn=sqlite3.connect(db_path)
query='SELECT * FROM Observation LIMIT 5;'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='SELECT * FROM Observation LIMIT 15;'
df1=pd.read_sql_query(query,conn)
print(df1)
```

```python
query='SELECT * FROM Observation WHERE tip>2;'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='SELECT * FROM Sex;'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='SELECT * FROM Observation WHERE sex_id=1 AND tip>2;'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='SELECT sum(total_bill) FROM Observation AS total_revenue;'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='SELECT sum(total_bill) FROM Observation WHERE sex_id=1;'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select count(*) from Observation;'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
conn=sqlite3.connect(db_path)
df=pd.read_sql_query('SELECT * FROM observation WHERE sex_id=0 AND day_id=0 AND time_id=0',conn)
print(df)
```

```python
conn=sqlite3.connect(db_path)
df=pd.read_sql_query('SELECT * FROM observation WHERE sex_id=0 and total_bill>10',conn)
print(df)
```

```python
df=pd.read_sql_query('SELECT * FROM observation WHERE smoker_id=1 AND day_id=3 AND total_bill>10',conn)
print(df)
```

```python
df=pd.read_sql_query('SELECT * FROM observation WHERE day_id=3 AND total_bill>10 AND tip>5',conn)
print(df)
```

```python
df=pd.read_sql_query('SELECT * FROM observation WHERE day_id=3 AND total_bill>10 AND tip>5 AND sex_id=0',conn)
print(df)
```

```python
query='select avg(tip) from observation;'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select day.day,avg(observation.tip) as avg_tip from observation join day on observation.day_id=day.day_id group by day.day;'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select smoker.smoker,avg(observation.tip) as avg_tip from observation join smoker on observation.smoker_id=smoker.smoker_id group by smoker.smoker;'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select sex.sex,avg(observation.tip) as avg_tip from observation join sex on observation.sex_id=sex.sex_id group by sex.sex;'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select time.time,avg(observation.tip) as avg_tip from observation join time on observation.time_id=time.time_id group by time.time;'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select day.day,avg(observation.tip) as avg_tip from observation join day on observation.day_id=day.day_id group by day.day;'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select total_bill,avg(tip) as avg_tip from observation group by total_bill limit 5;'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select total_bill,avg(tip) as avg_tip from observation group by total_bill limit 1;'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select * from observation where smoker_id=1 limit 10;'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select * from observation where total_bill>20 and tip>5;'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select tip, case when tip>5 then "High" when tip between 3 and 5 then "Medium" else "Low" end as tip_category from observation;'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select day, case when day in ("Saturday","Sunday") then "Weekend" else "Weekday" end as day_category from day;'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select round(avg(tip),2) as avg_tip from observation;'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select sum(total_bill) as total_revenue from observation '
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select count(*) as total_records from observation;'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
conn.close()
```

***Running the code file***
```bash
uv run main.py
```