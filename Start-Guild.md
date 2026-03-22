# Syntax

## Panda
```python
import panda as pd
```

## How to read data
### The codes are as follows:
```python
# save filepath to variable for easier access
melbourne_file_path = '../input/melbourne-housing-snapshot/melb_data.csv'
# read the data and store data in DataFrame titled melbourne_data
melbourne_data = pd.read_csv(melbourne_file_path) 
# print a summary of the data in Melbourne data
melbourne_data.describe()
```
<img width="1581" height="453" alt="image" src="https://github.com/user-attachments/assets/6238b429-f4e7-4fe3-a8d5-3f8ff8938601" />



