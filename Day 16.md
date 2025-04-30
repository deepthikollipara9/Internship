# Day 16 - 27 Feb 2025

1) Searched and explored what testing using pytest for csv files
2) Learned about the pytest module in Python for csv files.
3) Understood how to use pytest code to write testing  file.
4) Used chatgpt to understand few unknown topic in testing
     - Log in tho [chartgpt](https://openai.com/index/chatgpt/)
     - Upload the question you have doughts in
      ```
         Explain the above question in detail
      ```
5) uploading csv files and using pytest function and giving chatgpt to generate the question
6) Using chartgpt to generate the quires
      ```
        Give me the some sample question on pytest function
      ```

# Exercise

***Uploaded a dataset ***

```python
import pandas as pd
import pytest

def load_housing_data():
  file_path='housing.csv'
  return pd.read_csv(file_path)
```

***Checking if the dataset is empty or not***

```python
def test_dataframe_not_empty():
  df=load_housing_data()
  assert not df.empty,'Failed :Dataframe is empty!'
```

***checking of missing values***

```python
def test_no_missing_values():
  df=load_housing_data()
  assert df.isnull().sum().sum() == 0, "Missing values found in the dataset"
```

***Display of columns ***

```python
def test_dataframe_column():
  df=load_housing_data()
  exp_column={'longitude','latitude','housing_median_age','total_rooms',
              'total_bedrooms','population','households','median_income',
              'median_house_value'}
  assert set(df.columns)==exp_column,'Failed :Dataframe does not contain expected columns!'
```

***Display of valid coordinate***

```python
def test_valid_coordinate():
  df=load_housing_data()
  assert df['latitude'].between(-90,90).all() and df['longitude'].between(-180,180).all(),'Failed :Invalid coordinates found'
```

***Display of housing age range***

```python
def test_housing_age_range():
  df=load_housing_data()
  assert df['housing_median_age'].between(0,100).all(),'Failed :Invalid housing median age range'
```

***Display of non negative values***

```python
def test_non_negative_values():
  df=load_housing_data()
  numeric_columns=['total_rooms','total_bedrooms','population','households','median_income','median_house_value']
  assert (df[numeric_columns]>=0).all().all(),'Failed :Negative values found in numeric columns'
```

***Display of house value range***

```python
def test_house_value_range():
  df=load_housing_data()
  assert df['median_house_value'].between(10000,500000).all(),'Failed :Invalid house value range'
```

***Display of population greater than household***

```python
def test_population_greater_than_household():
  df=load_housing_data()
  assert (df['population']>=df['households']).all(),'Failed :Population is less than households'
```

***Display of bedrooms less than rooms***

```python
def test_bedrooms_less_than_rooms():
  df=load_housing_data()
  assert (df['total_bedrooms']<=df['total_rooms']).all(),'Failed :Bedrooms are more than rooms'
```

***Display of median income range***

```python
def test_median_income_range():
  df=load_housing_data()
  assert df['median_income'].between(0,20).all(),'Failed :Invalid median income range'
```

***Display of column data type***

```python
def test_column_data_type():
  df=load_housing_data()
  assert all(df.dtypes=='float64'),'Failed :Invalid data type found'
```

***Display of rooms per household***

```python
def test_rooms_per_household():
  df=load_housing_data()
  df['rooms_per_household']=df['total_rooms']/df['households']
  assert df['rooms_per_household'].between(0,10).all(),'Failed :Invalid rooms per household ratio'
```

***Display of bedrooms per room***

```python
def test_bedrooms_per_room():
  df=load_housing_data()
  df['bedrooms_per_room']=df['total_bedrooms']/df['total_rooms']
  assert df['bedrooms_per_room'].between(0,10).all(),'Failed :Invalid bedrooms per room ratio'
```

***Display of population per household***

```python
def test_population_per_household():
  df=load_housing_data()
  df['population_per_household']=df['population']/df['households']
  assert df['population_per_household'].between(0,10).all(),'Failed :Invalid population per household ratio'
```

***Running the test***

```python
if __name__ == '__main__':
  test_functions=[
      test_dataframe_column,test_dataframe_not_empty,test_no_missing_values,
      test_valid_coordinate,test_housing_age_range,test_population_greater_than_household,
      test_bedrooms_less_than_rooms,test_non_negative_values,test_house_value_range,
      test_median_income_range,test_column_data_type,test_rooms_per_household,test_bedrooms_per_room,
      test_population_per_household
  ]
  for test in test_functions:
    try:
      test()
      print(f'{test.__name__} passed!')
    except AssertionError as e:
      print(f'{test.__name__} failed: {e}')
```
