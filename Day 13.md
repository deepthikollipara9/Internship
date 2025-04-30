# Day 13 - 24 Feb 2025

1) Searched and explored what testing is and how it works in Python.
2) Learned about the testing module in Python .
3) Understood how to use testing code to write testing  file.
4) Used chatgpt to understand few unknown topic in testing
     - Log in tho [chartgpt](https://openai.com/index/chatgpt/)
     - Upload the question you have doughts in
      ```
         Explain the above question in detail
      ```
5) Creating a dataset using testing function and giving chatgpt to generate the question
6) Using chartgpt to generate the quires
      ```
        Give me the some sample question on test function
      ```

# Exercise

***Creating a dataset of movies***

```python
import pandas as pd
def create_movie_reviews():
  data=[{"Movies":'Inception',"Year":2010,"Male Leads":'Leonardo Dicaprio',"Female Leads":'Elliot Page',"Review":'Scifi'},
        {"Movies":'Titanic',"Year":1997,"Male Leads":'Leonardo Dicaprio',"Female Leads":'Kate Winslet',"Review":'Loe story'},
        {"Movies":'Avatar',"Year":2009,"Male Leads":'Sam Worthington',"Female Leads":'Zoe Saldana',"Review":'Visually Stunning'},
        {"Movies":'The dark knight',"Year":2008,"Male Leads":'Christian Bale',"Female Leads":'Maggie Gyllenhaal',"Review":'Batman movie'},
        {"Movies":'Interstellar',"Year":2014,"Male Leads":'Matthew Mcconaughey',"Female Leads":'Anne Hathaway',"Review":'Thought-provoking'},
        {"Movies":'The matrix',"Year":1999,"Male Leads":'Keanu Reeves',"Female Leads":'Carrie Anne Moss',"Review":'Scifi'},
        {"Movies":'Forrest gump',"Year":1994,"Male Leads":'Tom Hanks',"Female Leads":'Robin Wright',"Review":'Heartwarming'},
        {"Movies":'Gladiator',"Year":2000,"Male Leads":'Russell Crowe',"Female Leads":'Connie Nielsen',"Review":'Epic Historical'},
        {"Movies":'The godfather',"Year":1972,"Male Leads":'Marlon Brando',"Female Leads":'Diane Keaton',"Review":'Classic gangster'},
        {"Movies":'Pulp fiction',"Year":1994,"Male Leads":'John Travolta',"Female Leads":'Uma Thurman',"Review":'Quentins best'},
        {"Movies":'Fight Club',"Year":1999,"Male Leads":'Brad Pitt',"Female Leads":'Helena Bonham Carter',"Review":'Cult Classic'},
        {"Movies":'The shawshank redemption',"Year":1994,"Male Leads":'Tim Robbins',"Female Leads":'Morgon Freeman',"Review":'Inspirational'},
        {"Movies":'The avengers',"Year":2012,"Male Leads":'Robert Downey Jr.',"Female Leads":'Scarlett Johansson',"Review":'Superhero Spectacle'},
        {"Movies":'Joker',"Year":2019,"Male Leads":'Joaquin Phoenix',"Female Leads":'Zazie Beetz',"Review":'Dark and intense'},
        {"Movies":'La La Land',"Year":2016,"Male Leads":'Ryan Gosling',"Female Leads":'Emma Stone',"Review":'Musical Brilliance'}]
  df = pd.DataFrame(data)
  with open ('movie_review.csv','w') as file:
      df.to_csv(file,index=False)
      print('Movie review sucessfull!')
  return df
```

*** Display the file***

```python
def display_movie_reviews():
  with open('movie_review.csv','r') as file:
    df=pd.read_csv(file)
    print(df)
display_movie_reviews()
```

***Create an movie reviews***

```python
def test_create_movie_reviews():
  df=create_movie_reviews()
  if not isinstance(df,pd.DataFrame):
    print('Failed: create_movie_reviews should return a DataFrame')
  if df.empty:
    print('Failed: DataFrame is empty')
  if not all(isinstance(x,int) for x in df['Year']):
    print('Failed: Year should be integer')
  if not all(isinstance(x,str) for x in df['Movies']):
    print('Failed: Movies should be string')
  if not all (isinstance(x,str) for x in df['Male Leads']):
    print('Failed: Male Leads should be string')
  if not all (isinstance(x,str) for x in df['Female Leads']):
    print('Failed: Female Leads should be string')
  if not all (isinstance(x,str) for x in df['Review']):
    print('Failed: Review should be string')
```

***Checking if the dataframe is empty or not***

```python
def test_dataframe_not_empty():
  df= create_movie_reviews()
  if df.empty:
    print('Failed: DataFrame is empty')
  print('Testpass: DataFrame is not empty')
```

***Display of unique movie name***

```python
def test_unique_movies():
  df=create_movie_reviews()
  if not df['Movies'].is_unique:
    print('Failed: Movies column should be unique')
  print('Testpass: Movies column is unique')
```

***Display of movies release after 2005***

```python
def test_movies_after_2005():
  df=create_movie_reviews()
  movies_after_2005=df[df['Year']>2005]
  if movies_after_2005.empty:
    print('Failed: No movies released after 2005')
  print('Testpass: Movies released after 2005')
```

***Display of movie name starting with 'T'***

```python
def test_movies_starting_with_T():
  df=create_movie_reviews()
  movies_starting_with_T=df[df['Movies'].str.startswith('T')]
  if movies_starting_with_T.empty:
    print('Failed: No movies starting with T')
  print('Success: Found {} movies starting with T'.format(len(movies_starting_with_T)))
```

***Display of movie name of same costars***

```python
def test_movies_with_same():
  df=create_movie_reviews()
  movies_with_same=df[df['Male Leads']==df['Female Leads']]
  if movies_with_same.empty:
    print('Failed: No movies with same male and female leads')
  print('Success: Found {} movies with same male and female leads'.format(len(movies_with_same)))
```

***Display of movie name of actor 'Leonardo'***

```python
def test_movies_with_leonardo():
  df=create_movie_reviews()
  movies_with_leonardo=df[(df['Male Leads']=='Leonardo Dicaprio')]
  if movies_with_leonardo.empty:
    print('Failed: No movies with Leonardo Dicaprio as male lead')
  print('Success: Found {} movies with Leonardo Dicaprio as male lead'.format(len(movies_with_leonardo)))
```

***Display of movie name of actor 'Scarlett'***

```python
def test_movie_with_scarlett():
  df=create_movie_reviews()
  movie_with_scarlett=df[(df['Female Leads']=='Scarlett Johansson')]
  if movie_with_scarlett.empty:
    print('Failed: No movies with Scarlett Johansson as female lead')
  print('Success: Found {} movies with Scarlett Johansson as female lead'.format(len(movie_with_scarlett)))
```

***Display of movie name of 90's***

```python
def test_movies_from_90s():
  df=create_movie_reviews()
  movies_from_90s=df[(df['Year']>=1990) & (df['Year']<=1999)]
  if movies_from_90s.empty:
    print('Failed: No movies from the 90s')
  print('Success: Found {} movies from the 90s'.format(len(movies_from_90s)))
```

***Display of movie name with long names***

```python
def test_movies_with_long():
  df=create_movie_reviews()
  movies_with_long=df[df['Review'].str.contains('long')]
  if movies_with_long.empty:
    print('Failed: No movies with long in the review')
  print('Success')
```

***Display of movie name with specific review***

```python
def test_movies_with_specific_review():
  df=create_movie_reviews()
  movies_with_specific_review=df[df['Review']=='Scifi']
  if movies_with_specific_review.empty:
    print('Failed: No movies with Scifi review')
  print('Success: Found {} movies with Scifi review'.format(len(movies_with_specific_review)))
```

***Running the test***

```python
if __name__=='__main__':
  test_create_movie_reviews()
  test_dataframe_not_empty()
  test_unique_movies()
  test_movies_after_2005()
  test_movies_starting_with_T()
  test_movies_with_same()
  test_movies_with_leonardo()
  test_movie_with_scarlett()
  test_movies_from_90s()
  test_movies_with_long()
  test_movies_with_specific_review()
```
