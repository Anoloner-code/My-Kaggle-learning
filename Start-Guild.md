# Syntax

## Panda
```python
import panda as pd
```

## How to read data
### Store data(csv) into a varible and list out:
```python
# save filepath to variable for easier access
melbourne_file_path = '../input/melbourne-housing-snapshot/melb_data.csv'
# read the data and store data in DataFrame titled melbourne_data
melbourne_data = pd.read_csv(melbourne_file_path) 
# print a summary of the data in Melbourne data
melbourne_data.describe()
```
<img width="1581" height="453" alt="image" src="https://github.com/user-attachments/assets/6238b429-f4e7-4fe3-a8d5-3f8ff8938601" />

## Selecting data for modeling
### Choosing only columns:
```python
melbourne_file_path = '../input/melbourne-housing-snapshot/melb_data.csv'
melbourne_data = pd.read_csv(melbourne_file_path) 
melbourne_data.columns

# The Melbourne data has some missing values (some houses for which some variables weren't recorded.)
# We'll learn to handle missing values in a later tutorial.  
# Your Iowa data doesn't have missing values in the columns you use. 
# So we will take the simplest option for now, and drop houses from our data. 
# Don't worry about this much for now, though the code is:

# dropna drops missing values (think of na as "not available")
melbourne_data = melbourne_data.dropna(axis=0)
```
<img width="1350" height="272" alt="image" src="https://github.com/user-attachments/assets/64665374-a27b-4928-9e99-c1d316d8c0e5" />

## Selecting The Prediction Target (As $${\color{Red}Y}$$)
### To select specific column, for example, to choose price:
```python
y = melbourne_data.Price
```

## Selecting features
### > The columns that are inputted into our model (and later used to make predictions) are called "features."
