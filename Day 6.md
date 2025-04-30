# Day 6 - 12 Feb 2025

1) Exporing how to add csv file to colab notebook from  [youtube](https://www.youtube.com/watch?v=ZjO-DFVdbeQ)
2) Exporing function on csv file to colab notebook from  [youtube](https://www.youtube.com/watch?v=dUpyC40cF6Q&list=PLUaB-1hjhk8GZOuylZqLz-Qt9RIdZZMBE)
3) Downloading dump database from the colab notebook which is present
4) Load rage the dump database to colab by write a query
5) Generated sample questions using chatgpt
    - login to [ChatGPT](https://openai.com/index/chatgpt/)
    - Upload the database dump to chatgpt to analyze
    - Written the prompt to generate sample questions
        ```
        Generate few sqlite question the given database 
        ```
6) Used chatgpt to understand few unknown topic in sql
     - Upload the question you have doughts in
    ```
        Explain the above question in detail
    ```
 # Execises

***Uploading file***

```python
from google.colab import files
uploaded=files.upload()
```

```python
import pandas as pd
df_housing=pd.read_csv("california_housing_test.csv")
```

```python
print(df_housing.head()))
```

***Checking for missing values***

```python
print(df_housing.isnull().sum())
```

***Creating a new column: Average per household***

```python
a=df_housing['Avg_per_household']=df_housing['total_rooms']/df_housing['households']
print(a)
```

***Finding the correlation between variables***

```python
print(df_housing.corr())
```

***Filtering data : Houses with median price above $300000***

```python
expensive_houses=df_housing[df_housing['median_house_value']>300000]
print(expensive_houses)
```

***Grouping by median aged houses and finding avg houses value***

```python
grouped_data=df_housing.groupby('housing_median_age')['median_house_value'].mean()
print(grouped_data)
```

***Sorting dataset by median income in descending order***

```python
df_sorted=df_housing.sort_values(by='median_income',ascending=False)
print(df_sorted)
```

***Finding the top 10 locations with the higest median house values***

```python
top_loca=df_housing.nlargest(10,'median_house_value')[['longitude','latitude','median_house_value']]
print(top_loca)
```

***Finding number of unique values of categorical columns***

```python
unique_count=df_housing.nunique()
print(unique_count)
```

***Create a price category column (low,medium,high)***

```python
df_housing['price_category']=pd.cut(df_housing['median_house_value'],
                                    bins=[0,150000,300000,df_housing['median_house_value'].max()],
                                    labels=['low','medium','high'])
print(df_housing['price_category'].value_counts())
```

***Compute the average number of bedrooms per total room***

```python
df_housing['Bedroom_ratio']=df_housing['total_bedrooms']/df_housing['total_rooms']
print(df_housing['Bedroom_ratio'].describe())
```

***Finding locations with the highest population density***

```python
df_housing['population_density']=df_housing['population']/df_housing['households']
highest_density=df_housing.nlargest(10,'population_density')[['longitude','latitude','population_density']]
print(highest_density)
```

***Find areas with median income greater than 5 and house value above 400000***

```python
high_income_high_value=df_housing[(df_housing['median_income']>5)&(df_housing['median_house_value']>400000)]
print(high_income_high_value.head())
```

***Get the median house valuse for each unique latitude-longitude pair***

```python
location_prices=df_housing.groupby(['latitude','longitude'])['median_house_value'].median()
print(location_prices.head())
```

***Normalizing median house value using min-max scaling***

```python
df_housing['normalized_house_value']=((df_housing['median_house_value']-df_housing['median_house_value'].min())/
                                      (df_housing['median_house_value'].max()))
print(df_housing[['normalized_house_value','median_house_value']].head())
```

***Find areas with an unusually high number of rooms per household***

```python
df_housing['rooms_per_household']=df_housing['total_rooms']/df_housing['households']
high_room_area=df_housing[df_housing['rooms_per_household']>df_housing['rooms_per_household'].quantile(0.99)]
print(high_room_area)
```

***Create new feature: population per bedroom***

```python
df_housing['population_per_bedroom']=df_housing['population']/df_housing['total_bedrooms']
print(df_housing[['population_per_bedroom']].describe())
```

***Sorting***

Selecting specific columns
```python
subset_column=df_housing[['longitude','latitude','median_house_value']]
print(subset_column)
```

Selecting first 5 rows
```python
subset_row=df_housing.iloc[0:5]
print(subset_row)
```

Selecting specific rows and columns
```python
sebset_rc=df_housing.loc[0:5,['longitude','latitude']]
print(sebset_rc)
```

Selecting all rows but only specific columns
```python
subset_all=df_housing.loc[:,['median_income','housing_median_age']]
print(subset_all)
```

Sorting by median house values in ascending order
```python
df_sort1=df_housing.sort_values(by='median_house_value',ascending=True)
print(df_sort1)
```

Sorting by multiple coloumns(first by income, then by house values)
```python
df_sort2=df_housing.sort_values(by=['median_income','median_house_value'],ascending=[False,True])
print(df_sort2)
```

Sorting by population in descending order
```python
df_sort3=df_housing.sort_values(by='population',ascending=False)
print(df_sort3)
```

***Slicing***

Slicing first 10 rows
```python
df_slice1=df_housing.iloc[0:10]
print(df_slice1)
```

Slicing last 10 rows
```python
df_slice2=df_housing.iloc[-10:]
print(df_slice2)
```

Slicing using index range
```python
df_slice3=df_housing.iloc[10:20,:]
print(df_slice3)
```

Slicing a specific column range
```python
df_slice4=df_housing.iloc[:,2:6]
print(df_slice4)
```

***Filtering data***

Filtering houses with a median value above $300000
```python
exp_house=df_housing[df_housing['median_house_value']>300000]
print(exp_house)
```

Filtering houses with high median income (>5) and low median house value(<200000)
```python
filter_house=df_housing[(df_housing['median_income']>5)&
                        (df_housing['median_house_value']<200000)]
print(filter_house)
```

Filtering houses within specific langitude and latitude
```python
costal_house=df_housing[(df_housing['longitude']<-120)&(df_housing['latitude']>30)]
print(costal_house.head())
```

Filtering housing with specific median age range (between 20 and 50)
```python
age_filtering=df_housing[(df_housing['housing_median_age']>=20)&(df_housing['housing_median_age']<=50)]
print(age_filtering)
```

Filtering houses where total rooms are above the average
```python
above_avg=df_housing[(df_housing['total_rooms']>df_housing['total_rooms'].mean())]
print(above_avg)
```

***Handling missing data***

Dropping row with missing values
```python
df_drop=df_housing.dropna()
print(df_drop)
```

Filling missing values with mean of columns
```python
numeric_df=df_housing.select_dtypes(include=['number'])
df_filled=df_housing.fillna(numeric_df.mean())
print(df_filled.head())
```

Replacing missing values in a specific columns with it median
```python
df_housing['total_bedroom']=df_housing['total_bedrooms'].fillna(df_housing['total_bedrooms'].median(),inplace=True)
print(df_housing.head())
```
