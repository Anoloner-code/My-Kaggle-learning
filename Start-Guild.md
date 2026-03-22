# Syntax

## Panda
```python
import pandas as pd
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
> ### The columns that are inputted into our model (and later used to make predictions) are called "features."
```python
melbourne_features = ['Rooms', 'Bathroom', 'Landsize', 'Lattitude', 'Longtitude']
```
###  We called this as  $${\color{lightblue}X}$$
```python
X = melbourne_data[melbourne_features]
X.describe()
```
<img width="698" height="418" alt="image" src="https://github.com/user-attachments/assets/73ff30e6-7a8e-4f87-86c0-9afddbe2bc08" />

### Use `.head()` to get the top few rows
<img width="698" height="297" alt="image" src="https://github.com/user-attachments/assets/035951b2-dd07-4416-9c06-c1121fe31ec7" />

## Concept
### We are using X (input) to get Y (Prediction result) 
### ML in a nutshell:
```python
model = SomeModel()
model.fit(X, y)
predictions = model.predict(X)
```
### Then Translate into our language:
### “Create a brain”
``` python
# Define model. Specify a number for random_state to ensure same results each run
melbourne_model = DecisionTreeRegressor(random_state=1)
```
### “Train the brain using examples”
```python
# Fit model
melbourne_model.fit(X, y)
```
### More specifically, in their terms we call this process in steps:
- **Define**: What type of model will it be? A decision tree? Some other type of model? Some other parameters of the model type are specified too.
- **Fit**: Capture patterns from provided data. This is the heart of modeling.
- **Predict**: It's just, predict, yeah.
- **Evaluate**: Determine how accurate the model's predictions are.

## Model Validation
### To know the error, more specifically, how far is your model predictions from the actual result:
```python
from sklearn.metrics import mean_absolute_error

predicted_home_prices = melbourne_model.predict(X)
mean_absolute_error(y, predicted_home_prices)
```
** The scikit-learn library has a function train_test_split to break up the data into two pieces.**
** We'll use some of that data as training data to fit the model, and we'll use the other data as validation data to calculate mean_absolute_error.**
```python
from sklearn.model_selection import train_test_split

# split data into training and validation data, for both features and target
# The split is based on a random number generator. Supplying a numeric value to
# the random_state argument guarantees we get the same split every time we
# run this script.
train_X, val_X, train_y, val_y = train_test_split(X, y, random_state = 0)
# Define model
melbourne_model = DecisionTreeRegressor()
# Fit model
melbourne_model.fit(train_X, train_y)

# get predicted prices on validation data
val_predictions = melbourne_model.predict(val_X)
print(mean_absolute_error(val_y, val_predictions))
```















