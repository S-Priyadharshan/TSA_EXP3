# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
Name: Priyadharshan S
Date: 02/09/2025


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
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

df = pd.read_csv("/content/co2_gr_mlo.csv", comment="#")

co2 = df['ann inc'].tolist()

n=len(co2)
print(n)

lags = range(35)

autocorr_values = []

mean_data = np.mean(co2)

variance_data = np.var(co2)

normalized_data = (co2 - mean_data) / np.sqrt(variance_data)

for lag in lags:
  if lag == 0:
    autocorr_values.append(1)
  else:
    auto_cov = np.sum((co2[:-lag] - mean_data) * (co2[lag:] - mean_data)) / n
    autocorr_values.append(auto_cov / variance_data)

plt.figure(figsize=(10, 6))
plt.stem(lags, autocorr_values)
plt.title('Autocorrelation of Data')
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')
plt.grid(True)
plt.show()
```

### OUTPUT:
<img width="857" height="547" alt="image" src="https://github.com/user-attachments/assets/0ad4e632-d1e9-4581-beda-9827c1a7ddab" />

### RESULT:
        Thus we have successfully implemented the auto correlation function in python.
