# Day 12 - 21 Feb 2025

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
5) Creating a dataset using json function and giving chatgpt to generate the question
6) Using chartgpt to generate the quires
      ```
        Give me the some sample question on json function
      ```
7) Deep understanding through the [youtube](https://www.youtube.com/watch?v=9N6a-VLBa2I)

# Exercise

***Creating a dataset of movies***

```python
import json
def create_movie_review():
  reviews = [
      {'title': 'inception', 'review': 'stunning visuals', 'year': 2010},
      {'title': 'the matrix', 'review': 'sci-fi masterpiece', 'year': 1999},
      {'title': 'interstellar', 'review': 'space exploration movie', 'year': 2014},
      {'title': 'the dark knight', 'review': 'super hero movie', 'year': 2008},
      {'title': 'tenet', 'review': 'complex thriller', 'year': 2020}
  ]
  with open('movie_review.json', 'w') as file:
    json.dump(reviews, file, indent=4)
    print('movie review created successfully')
create_movie_review()
```

*** Displaying the dataset***

```python
def display_movie_review():
  try:
    with open('movie_review.json', 'r') as file:
      reviews = json.load(file)
      for review in reviews:
        print(f"Title: {review['title']}")
        print(f"Review: {review['review']}")
        print(f"Year: {review['year']}")
        print()
  except FileNotFoundError:
    print('movie review not found')
display_movie_review()
```

***In the test_movie_review() function, why is there a try-except block when opening the file? What specific exceptions are being handled?***

```python
import os
def test_moive_review():
  print('testing movie review')
  if os.path.exists('movie_review.json'):
    print('movie review found')
  else:
    print('movie review not found')
    raise Exception('movie review not found')
  return True
```
```python
import os
def test_moive_review():
  print('testing movie review')
def test_movie_review(): #Corrected function name
    print('testing movie review')
    try:
        with open('movie_review.json', 'r') as file:
            reviews = json.load(file) #Try to load json data
            print("movie review found")
            return True
    except FileNotFoundError:
        print('movie review file not found')
        return False #return False on failure
    except json.JSONDecodeError: #Catch JSON errors
        print("Invalid JSON data in the file")
        return False

test_movie_review()
```

***What is the purpose of the test_year_after_2009() function? What kind of validation is it performing on the data?***

```python
import os
def test_movie_review():
    print('testing movie review')

def test_year_after_2009():
    print("Testing if movie year is after 2009")
    try:
        with open('movie_review.json', 'r') as file:
            reviews = json.load(file)
            for review in reviews:
                if review['year'] > 2009:
                    print(f"Movie '{review['title']}' released after 2009")
                    return True # Found a movie released after 2009
            print("No movie found released after 2009")
            return False
    except FileNotFoundError:
        print("Movie review file not found")
        return False
    except KeyError:
        print("Error: 'year' key not found in a movie review")
        return False
    except json.JSONDecodeError:
        print("Invalid JSON data in the file")
        return False

test_year_after_2009()
```

***In the add_movie_review() function, what happens if movie_review.json does not already exist? How is that handled?***

```python
import json
import os

def add_movie_review(title, review, year):
    try:
        with open('movie_review.json', 'r') as file:
            reviews = json.load(file)
    except FileNotFoundError:
        reviews = []

    new_review = {'title': title, 'review': review, 'year': year}
    reviews.append(new_review)

    with open('movie_review.json', 'w') as file:
        json.dump(reviews, file, indent=4)
    print(f"Review for '{title}' added successfully!")

add_movie_review("The Shawshank Redemption", "An inspiring tale of hope and friendship.", 1994)
```

***How does the update_movie_review() function ensure only the review for the specified movie gets updated?***

```python
def update_movie_review(title, new_review, new_year):
    try:
        with open('movie_review.json', 'r') as file:
            reviews = json.load(file)
    except FileNotFoundError:
        print("Movie review file not found.")
        return

    updated = False
    for review in reviews:
        if review['title'] == title:
            review['review'] = new_review
            review['year'] = new_year
            updated = True
            break

    if updated:
        with open('movie_review.json', 'w') as file:
            json.dump(reviews, file, indent=4)
        print(f"Review for '{title}' updated successfully!")
    else:
        print(f"Movie '{title}' not found in the reviews.")

update_movie_review("inception", "A mind-bending thriller", 2010)
```

***In the delete_movie_review() function, how does the use of list comprehension help in removing the targeted movie***

```python
import json

def delete_movie_review(title):
    try:
        with open('movie_review.json', 'r') as file:
            reviews = json.load(file)
    except FileNotFoundError:
        print("Movie review file not found.")
        return

    original_length = len(reviews)
    reviews = [review for review in reviews if review['title'] != title]

    if len(reviews) < original_length:
        with open('movie_review.json', 'w') as file:
            json.dump(reviews, file, indent=4)
        print(f"Review for '{title}' deleted successfully!")
    else:
        print(f"Movie '{title}' not found in the reviews.")


delete_movie_review("tenet")
```

***How is movie length added and used in the sort_reviews_by_movie_length() function? Is this length already in the file or added during processing?***

```python
import json

def sort_reviews_by_movie_length(filename="movie_review.json"):
    try:
        with open(filename, 'r') as file:
            reviews = json.load(file)
    except FileNotFoundError:
        print(f"Error: File '{filename}' not found.")
        return

    for review in reviews:
        if review['title'] == 'inception':
            review['length'] = 148  # Example length
        elif review['title'] == 'the matrix':
            review['length'] = 136
        elif review['title'] == 'interstellar':
            review['length'] = 169
        elif review['title'] == 'the dark knight':
            review['length'] = 152
        elif review['title'] == 'The Shawshank Redemption':
            review['length'] = 142
        else:
            review['length'] = 0

    # Sort reviews by length (longest to shortest)
    sorted_reviews = sorted(reviews, key=lambda x: x.get('length', 0), reverse=True)

    # Print the sorted reviews
    for review in sorted_reviews:
        print(f"Title: {review['title']}, Length: {review.get('length', 'N/A')}, Review: {review['review']}, Year: {review['year']}")


sort_reviews_by_movie_length()
```
