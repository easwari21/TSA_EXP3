# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
## Date: 27.04.2026

### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.

### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.

### PROGRAM:
```
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd

data=pd.read_csv('customer.csv')
data = data['Income'].tolist()

N = len(data)
lags = range(35)


autocorr_values = []

mean_data = np.mean(data)

variance_data = np.var(data)

normalized_data = (data - mean_data) / np.sqrt(variance_data)

for lag in lags:
    if lag == 0:
        autocorr_values.append(1)
    else:
        auto_cov = np.sum((data[:-lag] - mean_data) * (data[lag:] - mean_data)) / N 
        autocorr_values.append(auto_cov / variance_data)  # Normalize by variance

plt.figure(figsize=(10, 6))
plt.stem(lags, autocorr_values)
plt.title('Autocorrelation of Data')
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')
plt.grid(True)
plt.show()
```

### OUTPUT:

<img width="846" height="545" alt="download" src="https://github.com/user-attachments/assets/3e6ea3cc-2917-4e2e-955a-525bbc10b94b" />

### RESULT:

Thus we have successfully implemented the auto correlation function in python.
