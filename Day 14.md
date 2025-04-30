# Day 14 - 25 Feb 2025

1) Searched and explored what testing is and how it works in Python.
2) Learned about the testing module in Python .
3) Understood how to use testing code to write testing  file.
4) Learning how to use testing on csv files
5) Used chatgpt to understand few unknown topic in testing
     - Log in tho [chartgpt](https://openai.com/index/chatgpt/)
     - Upload the question you have doughts in
      ```
         Explain the above question in detail
      ```
6) Creating a dataset using testing function and giving chatgpt to generate the question
7) Using chartgpt to generate the quires
      ```
        Give me the some sample question on test function
      ```

# Exercise

***Uploaded a dataset ***

```python
import pandas as pd
from google.colab import files

uploaded = files.upload()

def read_csv_file(csv_filename='housing.csv'):
    df = pd.read_csv(csv_filename)
    return df
```

***Checking if the dataset is empty or not***

```python
def test_csv_dataframe(housing_csv):
  df=read_csv_file(housing_csv)
  if df.empty:
    print('Failed: DataFrame is empty')
  print('Testpass: DataFrame is not empty')
```

***checking of missing values***

```python
def test_csv_missing_value(housing_csv):
  df=read_csv_file(housing_csv)
  if df.isnull().values.any():
    print('Failed: DataFrame contains missing values')
  print('Testpass: DataFrame does not contain missing values')
```

***Display of median house value positive ***

```python
def test_csv_median_house_value_positive(housing_csv):
  df=read_csv_file(housing_csv)
  if(df['median_house_value']<0).any():
    print('Failed: DataFrame contains negative median house values')
  print('Testpass: DataFrame does not contain negative median house values')
```

***Display of bedrooms less than rooms***

```python
def test_csv_bedrooms_less_than_rooms(housing_csv):
  df=read_csv_file(housing_csv)
  if (df['total_bedrooms']>df['total_rooms']).any():
    print('Failed: DataFrame contains invalid number of bedrooms')
  print('Testpass: DataFrame does not contain invalid number of bedrooms')
```

***Display of population greater than household***

```python
def test_csv_population_greater_than_household(housing_csv):
  df=read_csv_file(housing_csv)
  if (df['population']>df['households']).any():
    print('Failed: DataFrame contains invalid population or household values')
  print('Testpass: DataFrame does not contain invalid population or household values')
```

***Display of housing median age range***

```python
def test_csv_housing_median_age_range(housing_csv):
  df=read_csv_file(housing_csv)
  if (df['housing_median_age']<0).any() or (df['housing_median_age']>100).any():
    print('Failed: DataFrame contains invalid housing median age values')
  print('Testpass: DataFrame does not contain invalid housing median age values')
```

***Display of median income positive***

```python
def test_csv_median_income_positive(housing_csv):
  df=read_csv_file(housing_csv)
  if (df['median_income']<0).any():
    print('Failed: DataFrame contains negative median income values')
  print('Testpass: DataFrame does not contain negative median income values')
```

***Display of total rooms positive***

```python
def test_csv_total_rooms_positive(housing_csv):
  df=read_csv_file(housing_csv)
  if (df['total_rooms']<0).any():
    print('Failed: DataFrame contains negative total rooms values')
  print('Testpass: DataFrame does not contain negative total rooms values')
```

***Display of total bedroom positive***

```python
def test_csv_total_bedroom_positive(housing_csv):
  df=read_csv_file(housing_csv)
  if (df['total_bedrooms']<0).any():
    print('Failed: DataFrame contains negative total bedrooms values')
  print('Testpass: DataFrame does not contain negative total bedrooms values')
```

***Display of population positive***

```python
def test_csv_population_positive(housing_csv):
  df=read_csv_file(housing_csv)
  if (df['population']<0).any():
    print('Failed: DataFrame contains negative population values')
  print('Testpass: DataFrame does not contain negative population values')
```

***Running the test***

```python
if __name__=='__main__':
  test_csv_dataframe('housing.csv')
  test_csv_missing_value('housing.csv')
  test_csv_median_house_value_positive('housing.csv')
  test_csv_bedrooms_less_than_rooms('housing.csv')
  test_csv_population_greater_than_household('housing.csv')
  test_csv_housing_median_age_range('housing.csv')
  test_csv_median_income_positive('housing.csv')
  test_csv_total_rooms_positive('housing.csv')
  test_csv_total_bedroom_positive('housing.csv')
  test_csv_population_positive('housing.csv')
```
