### DEVELOPED BY: VINOD KUMAR S
### REGISTER NO: 212222240116
### DATE:

# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)

### AIM:
To Compute the Auto Correlation Function (ACF) of the coffee sales dataset for the first 35 lags to determine the model
type to fit the data.
### ALGORITHM:
1. Import the necessary packages.
2. Find the mean, variance and then implement normalization for the data.
3. Define a Function to Compute Autocorrelation Function (ACF).
4. Implement the correlation using necessary logic and obtain the results.
5. Compute the ACF Values.
6. Represent the result in graphical representation as given below.
### PROGRAM:

```python
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd

# Load the coffee sales data
file_path = 'coffeesales.csv'  # Ensure this is the correct path to your CSV file
coffee_sales_data = pd.read_csv(file_path,nrows=50)

# Extract the 'money' column (sales data)
sales_data = coffee_sales_data['money'].values

# Calculate mean and variance
mean_sales = np.mean(sales_data)
var_sales = np.var(sales_data)

# Normalize the data (subtract mean and divide by standard deviation)
normalized_sales = (sales_data - mean_sales) / np.sqrt(var_sales)

# Compute the ACF for the first 35 lags
def compute_acf(data, max_lag):
    acf_values = []
    n = len(data)
    for lag in range(max_lag + 1):
        if lag == 0:
            acf_values.append(1)  # ACF at lag 0 is always 1
        else:
            acf = np.corrcoef(data[:-lag], data[lag:])[0, 1]
            acf_values.append(acf)
    return acf_values

lags = range(35)
acf_values = compute_acf(normalized_sales, 34)

# Plot the ACF results
plt.figure(figsize=(10, 6))
plt.stem(lags, acf_values, use_line_collection=True)
plt.title('Autocorrelation Function (ACF) for Coffee Sales')
plt.xlabel('Lag')
plt.ylabel('ACF')
plt.grid(True)
plt.show()

```
<br>
<br>
<br>
<br>

### OUTPUT:

![Screenshot 2024-09-09 111829](https://github.com/user-attachments/assets/5f09b935-6339-4d42-adce-cda3b0b7a652)


### RESULT:
 Thus, the python code for implementing the auto correlation function is executed successfully.  
