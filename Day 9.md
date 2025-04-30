# Day 9 - 17 Feb 2025

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
import pandas as pd
import sqlite3
db_path='chinook.db'
conn=sqlite3.connect(db_path)
query='select * from customers'
df=pd.read_sql_query(query,conn)
print(df)
```

***Retrieve specific columns from table***

```python
query='select FirstName,LastName,Email from customers'
df=pd.read_sql_query(query,conn)
print(df)
```

***Count the number of rows in table***

```python
query='select count(*) from customers'
df=pd.read_sql_query(query,conn)
print(df)
```

***Get unqiue values from a column***

```python
query='select distinct country from customers'
df=pd.read_sql_query(query,conn)
print(df)
```

***Fliter records using where***

```python
query='select * from customers where country="India"'
df=pd.read_sql_query(query,conn)
print(df)
```

***Sorting results using order by***

```python
query='select firstname,lastname,country from customers order by lastname asc'
df=pd.read_sql_query(query,conn)
print(df)
```

***Limit the number of results***

```python
query='select * from tracks limit 10'
df=pd.read_sql_query(query,conn)
print(df)
```

***Find the highest paid track***

```python
query='select max(unitprice) from tracks'
df=pd.read_sql_query(query,conn)
print(df)
```

***Get all invoice for a specific customer***

```python
query='select * from invoices where customerid=9'
df=pd.read_sql_query(query,conn)
print(df)
```

***Get the total number of track***

```python
query='select count(*) from tracks'
df=pd.read_sql_query(query,conn)
print(df)
```

***Find all the employees how are sales representatives***

```python
query='select * from employees where title="Sales Support Agent"'
df=pd.read_sql_query(query,conn)
print(df)
```

***Get the total revenue from all invoice***

```python
query='select sum(total) from invoices'
df=pd.read_sql_query(query,conn)
print(df)
```

***Find the average price of all tracks***

```python
query = 'select avg(unitprice) from tracks'
df = pd.read_sql_query(query, conn)
print(df)
```

***Count the number of customers by country***

```python
query='select country,count(*) from customers group by country order by count(*) desc'
df=pd.read_sql_query(query,conn)
print(df)
```

***Find the top 3 more expensive tracks***

```python
query='select * from tracks order by unitprice desc limit 3'
df=pd.read_sql_query(query,conn)
print(df)
```

***Find the total number of invoices by customers***

```python
query='select customerid,count(*) from invoices group by customerid'
df=pd.read_sql_query(query,conn)
print(df)
```

***List all tracks with their corresponding genre***

```python
query='select tracks.name,genres.name from tracks join genres on tracks.genreid=genres.genreid'
df=pd.read_sql_query(query,conn)
print(df)
```

***Get all customers and their total spending***

```python
query='select customers.firstname,customers.lastname,sum(invoices.total) from customers join invoices on customers.customerid=invoices.customerid group by customers.customerid'
df=pd.read_sql_query(query,conn)
print(df)
```

***Find all tracks purchased in invoice***

```python
query='select distinct tracks.name from tracks join invoice_items on tracks.trackid=invoice_items.trackid'
df=pd.read_sql_query(query,conn)
print(df)
```

***Get the most sold track(based on quantity)***

```python
query='select tracks.name,sum(invoice_items.quantity) from tracks join invoice_items on tracks.trackid=invoice_items.trackid group by tracks.trackid order by sum(invoice_items.quantity) desc'
df=pd.read_sql_query(query,conn)
print(df)
```

***Find all the invioce from the year 2010***

```python
query='select * from invoices where strftime("%Y",invoicedate)="2010"'
df=pd.read_sql_query(query,conn)
print(df)
```

***Extract the first name and last name in upper case***

```python
query='select upper(firstname),upper(lastname) from customers'
df=pd.read_sql_query(query,conn)
print(df)
```

***Find all customers whoes name starts with 'J'***

```python
query='select * from customers where firstname like "J%"'
df=pd.read_sql_query(query,conn)
print(df)
```

***Get invoice details with formated date***

```python
query='select invoicedate,strftime("%d-%m-%Y",invoicedate) from invoices'
df=pd.read_sql_query(query,conn)
print(df)
```

***Find employees hired after 2005***

```python
query='select * from employees where hiredate>"2005"'
df=pd.read_sql_query(query,conn)
print(df)
```

***Retrive all tracks that are more than 5 mins***

```python
query='select * from tracks where milliseconds>300000'
df=pd.read_sql_query(query,conn)
print(df)
```

***Get the total number of playlist***

```python
query='select count(*) from playlists'
df=pd.read_sql_query(query,conn)
print(df)
```

***List all the media type in the playlist***

```python
query='select *  from playlists'
df=pd.read_sql_query(query,conn)
print(df)
```

***Find all the customer from Canada***

```python
query='select * from customers where country="Canada"'
df=pd.read_sql_query(query,conn)
print(df)
```

***Retrive the first 10 customers***

```python
query='select * from customers limit 10'
df=pd.read_sql_query(query,conn)
print(df)
```

***Finding all tracks that has the word love***

```python
query='select * from tracks where name like "%love%"'
df=pd.read_sql_query(query,conn)
print(df)
```

***Find the cheapest track***

```python
query='select min(unitprice) from tracks'
df=pd.read_sql_query(query,conn)
print(df)
```

***Retrive all the invoice above 20***

```python
query='select * from invoices where total>20'
df=pd.read_sql_query(query,conn)
print(df)
```

***Closing the cursor***

```python
conn.close()
```