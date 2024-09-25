### NAME:RAGUNATH R
### REGISTER N0: 212222240081
### Date: 

# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION

### AIM:
To Illustrates how to perform time series analysis and decomposition on the daily minimum temperature dataset

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Load the daily minimum temperatures dataset
data = pd.read_csv('/content/daily-minimum-temperatures-in-me.csv')

# Display the first five rows of the dataset
print("FIRST FIVE ROWS:")
print(data.head())

# Select the first 120 rows for analysis (adjust as per your needs)
data = data.head(120)

# Ensure that the 'Date' column is correctly formatted or create a date range if missing
data['Date'] = pd.date_range(start='1/1/1981', periods=len(data), freq='M')  # Monthly frequency

# Set the 'Date' column as the index
data.set_index('Date', inplace=True)

# Use the 'Daily minimum temperatures' column for seasonal decomposition
result = seasonal_decompose(data['Daily minimum temperatures'], model='additive', period=12)  # Yearly seasonality assumed

# Plot the original data
print("\nPLOTTING THE DATA:")
plt.figure(figsize=(10, 5))
plt.plot(data['Daily minimum temperatures'])
plt.title('Yearly Average Daily Minimum Temperatures Over Time')
plt.xlabel('Year')
plt.ylabel('Temperature')
plt.show()

# Plot the seasonal component
print("\nSEASONAL PLOT REPRESENTATION:")
plt.figure(figsize=(10, 5))
result.seasonal.plot()
plt.title('Seasonal Decomposition')
plt.ylabel('Seasonal Component')
plt.show()

# Plot the trend component
print("\nTREND PLOT REPRESENTATION:")
plt.figure(figsize=(10, 5))
result.trend.plot()
plt.title('Trend Decomposition')
plt.ylabel('Trend Component')
plt.show()

# Plot the overall decomposition: Observed, Trend, Seasonal, and Residual components
print("\nOVERALL REPRESENTATION:")
fig, (ax1, ax2, ax3, ax4) = plt.subplots(4, 1, figsize=(10, 10))
result.observed.plot(ax=ax1)
ax1.set_ylabel('Observed')
result.trend.plot(ax=ax2)
ax2.set_ylabel('Trend')
result.seasonal.plot(ax=ax3)
ax3.set_ylabel('Seasonal')
result.resid.plot(ax=ax4)
ax4.set_ylabel('Residual')
plt.tight_layout()
plt.show()
```


### OUTPUT:
![image](https://github.com/user-attachments/assets/e1d1cb2e-7ec4-4d99-9d61-d8b63c25c8c1)
![image](https://github.com/user-attachments/assets/f614ccaf-03c3-4635-a3fc-b3d54a4be2e2)
![image](https://github.com/user-attachments/assets/c6ed74ca-cb01-4b1c-8562-cbe0488ca95a)
![image](https://github.com/user-attachments/assets/99e34417-b8eb-4b84-ade2-4bef71bb6951)
![image](https://github.com/user-attachments/assets/f526ec1a-8b59-44e1-b08c-40faa35f2247)
![image](https://github.com/user-attachments/assets/da314f0e-f5ee-4854-b878-b2a364bd5a74)
![image](https://github.com/user-attachments/assets/c737ac41-aae4-4e24-ab6e-bdcad37d99c8)



### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
