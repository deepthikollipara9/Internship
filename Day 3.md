# Day 3- 06 Feb 2025

1) Exporing Google Colab Notebook from the official [site](https://colab.research.google.com/)
2) Knowing how does colab notebook work from the  [youtube](https://www.youtube.com/watch?v=WrB-ECT-y8c)
3) Practing few python programs
4) Generated sample questions using chatgpt
    - login to [ChatGPT](https://openai.com/index/chatgpt/)
    - Upload the database dump to chatgpt to analyze
    - Written the prompt to generate sample questions
        ```
        Generate few python question for practing
        ```
  5) Reading about pandas from [Geeksforgeeks](https://www.geeksforgeeks.org/pandas-tutorial/)

## Exercise

***Print statements***

```python
print ("welcome to  google colab")
```

***Print max values***

```python
a=7
b=5
print(max(a,b))
```

***Print factorial numbers***

```python
num=6
factorial=1
for i in range(1,num+1):
  factorial=factorial*i
print(f"the factorial of {num} is {factorial}")
```

***Print simple intrest amount***

```python
p=10000
r=5
t=5
si=(p*t*r)/100
print(si)
```

***Print sum of two number using def function***

```python
def add_numbers (num1,num2):
  sum = num1+num2
  print("sum: ",sum)

add_numbers(9,8)
```

***Converting kilometers to meters***

```python
km=float(input("enter the value in km:"))
con_fac=0.6213
miles=km*con_fac
print(miles,"miles")
```

***Creating a dataframe***

```python
import pandas as pd
my_dataset= {'car':['bmw','shift','ford','volvo'],
             'year':['2013','2007','2010','2009'],
             'capacity':['4','4','7','6']
}
my_var=pd.DataFrame(my_dataset)
print(my_var)
```

***Displaying pandas version***

```python
import pandas as pd
print (pd.__version__)
```

***Created a data with series***

```python
import pandas as pd
calories={'day1':500,'day2':430,'day3':470}
my_cal=pd.Series(calories)
print(my_cal)
```

***Printing only one value***

```python
print(my_cal[0])
```
