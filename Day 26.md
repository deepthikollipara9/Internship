# Day 26 - 13 March 2025

1) Upload the Database into the Project Folder
   -Place your database file (chinook.db) into your project folder (e.g., myproject)
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
db_path="chinook.db"
conn=sqlite3.connect(db_path)
```

```python
query='select * from customers'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select FirstName,LastName,Email from customers'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select count(*) from customers'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select distinct country from customers'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select * from customers where country="India"'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select firstname,lastname,country from customers order by lastname asc'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select * from tracks limit 10'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select max(unitprice) from tracks'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select count(*) from tracks'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select * from invoices where customerid=9'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select * from employees where title="Sales Support Agent"'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select sum(total) from invoices'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query = 'select avg(unitprice) from tracks'
df = pd.read_sql_query(query, conn)
print(df)
```

```python
query='select country,count(*) from customers group by country order by count(*) desc'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select * from tracks order by unitprice desc limit 3'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select customerid,count(*) from invoices group by customerid'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select tracks.name,genres.name from tracks join genres on tracks.genreid=genres.genreid'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select customers.firstname,customers.lastname,sum(invoices.total) from customers join invoices on customers.customerid=invoices.customerid group by customers.customerid'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select distinct tracks.name from tracks join invoice_items on tracks.trackid=invoice_items.trackid'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select tracks.name,sum(invoice_items.quantity) from tracks join invoice_items on tracks.trackid=invoice_items.trackid group by tracks.trackid order by sum(invoice_items.quantity) desc'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select * from invoices where strftime("%Y",invoicedate)="2010"'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select upper(firstname),upper(lastname) from customers'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select * from customers where firstname like "J%"'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select invoicedate,strftime("%d-%m-%Y",invoicedate) from invoices'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select * from employees where hiredate>"2005"'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select * from tracks where milliseconds>300000'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select count(*) from playlists'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select *  from playlists'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
query='select * from customers where country="Canada"'
df=pd.read_sql_query(query,conn)
print(df)
```

```python
conn.close()
```
