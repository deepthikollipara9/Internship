# Day 11 - 20 Feb 2025

1) Searched and explored what JSON is and how it works in Python.
2) Learned about the json module in Python which is used to work with JSON
data.
3) Understood how to use json.dump() to write JSON data to a file.
4) Used chatgpt to understand few unknown topic in json
     - Log in tho [chartgpt](https://openai.com/index/chatgpt/)
     - Upload the question you have doughts in
      ```
         Explain the above question in detail
      ```
5) Using chartgpt to generate the quires
      ```
        Give me the some sample question on json function
      ```
6) Deep understanding through the [website](https://realpython.com/python-json/)

# Exercise

***How can you handle Unicode characters in JSON data when writing to a file?***

```python
import json
data = {'name': '李雷', 'city': '北京'}
json_str = json.dumps(data, ensure_ascii=False)
print(json_str)
with open('unicode.json', 'w', encoding='utf-8') as f:
    json.dump(data, f, ensure_ascii=False, indent=2)
```

*** How do you handle nested JSON structures when reading from a file?***

```python
import json

nested_json = {
    "person": {
        "name": "John",
        "address": {
            "city": "New York",
            "zip": "10001"
        }
    }
}
# Write to a file
with open('nested.json', 'w') as f:
    json.dump(nested_json, f, indent=2)
# Read and access nested data
with open('nested.json') as f:
    data = json.load(f)
    print("City:", data['person']['address']['city'])
```

*** Convert dictionary into JSON string***

```python
import json
data = {'name': 'John', 'age': 30, 'city': 'New York'}
json_str = json.dumps(data)
print(json_str)
```

***Convert JSON string to Python dictionary***

```python
import json
json_data = '{"product": "Laptop", "price": 799, "available": true}'
parsed_data = json.loads(json_data)
print(parsed_data)
```

***Load data.json and print the value of the "name" key***

```python
import json
with open('data.json', 'r') as f:
    data = json.load(f)
    print("Name:", data['name'])
```

***Read movie list from file and print titles***

```python
import json
with open('movies.json', 'r') as f:
    movies = json.load(f)
for movie in movies:
    print("Title:", movie['title'])
```

***What is the output of json.dumps({"a": 1, "b": 2}, indent=2)***

```python
import json
result = json.dumps({"a": 1, "b": 2}, indent=2)
print(result)
```
```
  "a": 1,
  "b": 2
```

***Convert Python list to JSON string***

```python
import json
fruits = ['apple', 'banana', 'cherry']
json_list = json.dumps(fruits)
print(json_list)
```

*** Save and load a dictionary with nested lists***

```python
data = {
    'name': 'Anna',
    'scores': [95, 88, 76],
    'passed': True
}
# Save
with open('student.json', 'w') as f:
    json.dump(data, f, indent=4)
# Load
with open('student.json') as f:
    loaded = json.load(f)
    print(loaded)

```

***Append new record to existing JSON file***

```python
import json
# Load existing
with open('movies.json', 'r') as f:
    movies = json.load(f)
# Append new
movies.append({'title': 'Tenet', 'year': 2020})
# Save back
with open('movies.json', 'w') as f:
    json.dump(movies, f, indent=2)

```
