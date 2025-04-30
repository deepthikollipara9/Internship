# Day 15 - 26 Feb 2025

1) Searched and explored what testing using pytest
2) Learned about the pytest module in Python .
3) Understood how to use pytest code to write testing  file.
4) Used chatgpt to understand few unknown topic in testing
     - Log in tho [chartgpt](https://openai.com/index/chatgpt/)
     - Upload the question you have doughts in
      ```
         Explain the above question in detail
      ```
5) Creating a dataset using testing function and giving chatgpt to generate the question
6) Using chartgpt to generate the quires
      ```
        Give me the some sample question on pytest function
      ```

# Exercise

***Uploaded a dataset ***

```python
import pandas as pd
import pytest

def create_employee_dataframe():
  data={'Employee id':[1001,1002,1049,3943,2743,4773,5372,2423,2334,3421],
        'Name':['Alia','Bam','Cham','Ram','Eve','Alice','Bob','Frank','Bob','David'],
        'Phone_no':[12345,56332,56234,32224,74382,64842,74742,56423,44484,63542],
        'City':['Nyc','UK','USA','Nyc','Los angles','Chicago','Honkong','Dallas','Los angles','Dallas'],
        'Branch':['HR','Team lead','It','Finance','Marketing','It','HR','Team lead','Finance','Marketing']}
  return pd.DataFrame(data)
```

***Checking if the dataset is empty or not***

```python
def test_dataframe_not_empty():
  df=create_employee_dataframe()
  assert not df.empty,'Failed :Dataframe is empty!'
```

***checking of missing values***

```python
def test_no_missing_values():
  df=create_employee_dataframe()
  assert df.isnull().sum().sum(),'Failed :Dataframe contains missing values!'
```

***Display of columns ***

```python
def test_dataframe_columns():
  df=create_employee_dataframe()
  expected_columns=['Employee id','Name','Phone_no','City','Branch']
  assert list(df.columns)==expected_columns,'Failed :Dataframe does not contain expected columns!'
```

***Display of unique employee ids***

```python
def test_unique_employee_ids():
  df=create_employee_dataframe()
  assert df['Employee id'].is_unique,'Failed :Employee ids are not unique!'
```

***Display of duplication name***

```python
def test_duplication_name():
  df=create_employee_dataframe()
  duplicate_names=df['Name'].duplicated().sum()
  assert duplicate_names>0,'Failed :Duplicate names found!'
```

***Display of duplicate branch***

```python
def test_duplicate_branch():
  df=create_employee_dataframe()
  duplicate_branch=df['Branch'].duplicated().sum()
  assert duplicate_branch>1,'Failed :Duplicate branch found!'
```

***Display of duplicate cities***

```python
def test_duplicate_cities():
  df=create_employee_dataframe()
  duplicate_cities=df['City'].duplicated().sum()
  assert duplicate_cities>1,'Failed :Duplicate cities found!'
```

***Display of unqiue phone number***

```python
def test_unique_phone_no():
  df=create_employee_dataframe()
  assert df['Phone_no'].is_unique,'Failed :Duplicate phone numbers found!'
```

***Display of employee id range***

```python
def test_employee_id_range():
  df=create_employee_dataframe()
  assert df['Employee id'].between(1000,5000).all(),'Failed :Employee ids are out of range!'
```

***Display of empty name***

```python
def test_non_empty_name():
  df=create_employee_dataframe()
  assert df['Name'].str.strip().ne('').all(),'Failed :Empty names found!'
```

***Display of valid city names***

```python
def test_valid_city_names():
  df=create_employee_dataframe()
  valid_cities=['Nyc','UK','USA','Los angles','Chicago','Honkong','Dallas']
  assert set(df['City']).issubset(set(valid_cities)),'Failed :Invalid city names found!'
```

***Running the test***

```python
if __name__ == '__main__':
  test_functions=[
      test_dataframe_columns,test_unique_phone_no,test_dataframe_not_empty,test_no_missing_values,
      test_unique_employee_ids,test_duplication_name,test_duplicate_branch,test_duplicate_cities,test_unique_phone_no,
      test_employee_id_range,test_non_empty_name,test_valid_city_names
  ]

  for test in test_functions:
    try:
      test()
      print(f'{test.__name__} passed!')
    except AssertionError as e:
      print(f'{test.__name__} failed: {e}')
```
