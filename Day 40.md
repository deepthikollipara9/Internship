# Day 40 - 11 April 2025

1) Uploading the CSV File to Your Project Folder
    -jobs.csv 
    -Make sure the path is correct for our environment  
2) Reading the File with Optimization
3) Practicing Optimization Techniques
4) Asking Chartgpt to how to save the optimized csv file 
    -Logged into [ChatGPT](https://openai.com/index/chatgpt/)
     ```
     How to save the optimized file
     ```
5) Grouping all the same desired role , university names, and gender to optimize the csv by assigning them a value.  



#Exercises

***Writing down dependencies***
```python
# /// script
# requires-python = ">=3.11"
# dependencies = [
#   "matplotlib",
#   "numpy",
#   "pandas"
# ]
# ///
```

***Optimized Pandas***
```python
import pandas as pd
import numpy as np
```

***Efficient Data Loading with optimized dtypes***
```python
dtype_dict = {
    "longitude": "float32",
    "latitude": "float32",
    "housing_median_age": "int16",
    "total_rooms": "int32",
    "total_bedrooms": "int32",
    "population": "int32",
    "households": "int32",
    "median_income": "float32",
    "median_house_value": "int32",
}
```

```python
df= pd.read_csv("job_candidates.csv")
```

***gender***
```python
# Step 1: Define the mapping
gender_map = {
    'Female': 1,
    'Male': 2,
    'Other': 3
}
# Step 2: Replace values in the gender column
df['gender'] = df['gender'].map(gender_map)
# Step 3: Create the lookup table
gender_lookup = pd.DataFrame({
    'Gender_Label': ['Female', 'Male', 'Other'],
    'Gender_Code': [1, 2, 3]
})
# Step 4: Print confirmation
print("✅ Gender column updated with numeric codes.\n")
print("📘 Gender Lookup Table:")
print(gender_lookup)
```

***Desired role***
```python
# Step 1: Create mapping for desired_role
desired_role_map = {role: idx + 1 for idx, role in enumerate(df['desired_role'].dropna().unique())}
# Step 2: Encode the desired_role column
df['desired_role_code'] = df['desired_role'].map(desired_role_map)
# Step 3: Create the Desired Role Lookup Table
desired_role_lookup = pd.DataFrame({
    'Desired_Role': list(desired_role_map.keys()),
    'Desired_Role_Code': list(desired_role_map.values())
})
# Step 4: Print confirmation
print("✅ 'desired_role' column encoded successfully!\n")
print("📘 Desired Role Lookup Table:")
print(desired_role_lookup)
```

***University name***
```python
# Step 1: Create mapping for university_name
university_name_map = {uni: idx + 1 for idx, uni in enumerate(df['university_name'].dropna().unique())}
# Step 2: Encode the university_name column
df['university_name_code'] = df['university_name'].map(university_name_map)
# Step 3: Create the University Name Lookup Table
university_lookup = pd.DataFrame({
    'University_Name': list(university_name_map.keys()),
    'University_Code': list(university_name_map.values())
})
# Step 4: Print confirmation
print("\n✅ 'university_name' column encoded successfully!\n")
print("🏫 University Name Lookup Table:")
print(university_lookup)
```

***Createing the updated file***
```python
output_file = "job_candidates_optimized.csv"
df.to_csv(output_file, index=False)
print(f"✅ Optimized file saved as '{output_file}'")
```