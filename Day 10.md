# Day 10 - 19 Feb 2025

1) Searched and explored what JSON is and how it works in Python.
2) Learned about the json module in Python which is used to work with JSON
data.
3) Understood how to use json.dump() to write JSON data to a file.
4) Used chatgpt to understand few unknown topic in json
     - Log in the [chartgpt](https://openai.com/index/chatgpt/)
     - Upload the question you have doughts in
      ```
         Explain the above question in detail
      ```
5) What is JSON?
-JSON stands for JavaScript Object Notation
-It is a lightweight data format often used for storing and exchanging data
-It is easy for humans to read and write, and for machines to parse and generate
6) Deep understanding through the [website](https://www.w3schools.com/python/python_json.asp)

# Exercise

*** What does JSON stand for and what is it commonly used for?***

```
JavaScript Object Notation, used to exchange and store structured data.
```

*** Which Python module is used to work with JSON data?***

```python
import json
print("JSON module imported successfully!")
```

***How do you convert a Python dictionary into a JSON string?***

```python
import json
data = {'name': 'Alice', 'age': 25, 'city': 'Paris'}
json_str = json.dumps(data)
print(json_str)
```

***How do you write a JSON object to a file using Python?***

```python
import json
person = {'name': 'Bob', 'age': 30, 'country': 'USA'}
with open('person.json', 'w') as file:
    json.dump(person, file)
```

***How do you read a JSON file and convert it into a Python object?***

```python
import json
with open('person.json', 'r') as file:
    data = json.load(file)
    print(data)
```

***What is the difference between json.dump() and json.dumps()***

```python
import json
# dumps - returns a JSON string
person = {'name': 'Charlie', 'age': 28}
json_string = json.dumps(person)
print("Using dumps:", json_string)
# dump - writes JSON to a file
with open('charlie.json', 'w') as f:
    json.dump(person, f)
```

*** Which function is used to parse a JSON string back into a Python object?***

```python
import json
json_data = '{"product": "Laptop", "price": 799}'
parsed_data = json.loads(json_data)
print(parsed_data)
```

***What happens if your Python object contains a non-serializable value?***

```python
import json
data = {'numbers': {1, 2, 3}}  
try:
    json_str = json.dumps(data)
except TypeError as e:
    print("Error:", e)
```

***How can you pretty-print JSON data in a file?***

```python
import json
data = {'name': 'Eva', 'skills': ['Python', 'SQL'], 'active': True}
with open('pretty.json', 'w') as file:
    json.dump(data, file, indent=4)
```

***How would you read a list of JSON objects from a file and loop through them?***

```python
import json
# Sample JSON list
movie_list = [
    {'title': 'Inception', 'year': 2010},
    {'title': 'Interstellar', 'year': 2014}
]
# Write to file
with open('movies.json', 'w') as f:
    json.dump(movie_list, f, indent=2)
# Read from file and loop
with open('movies.json', 'r') as f:
    movies = json.load(f)
    for movie in movies:
        print(f"Title: {movie['title']}, Year: {movie['year']}")

```
