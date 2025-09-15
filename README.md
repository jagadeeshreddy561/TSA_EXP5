### Developed by : Mallu Jagadeeswar Reddy
### Register no. : 212222240059
### Date: 
# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION



### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average Volume of National Stocks Exchange.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:

```python
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

data = pd.read_csv('infy_stock.csv')
data.head()

data['Date'] = pd.to_datetime(data['Date'], errors='coerce')
data = data.dropna(subset=['Date'])
data.set_index('Date', inplace=True)

data['Volume'] = pd.to_numeric(data['Volume'], errors='coerce')

data = data.dropna(subset=['Volume'])

plt.plot(data['Volume'], label='Data')
plt.title('Plotting the Data')
plt.legend()
plt.show()

period = 13
result = seasonal_decompose(data['Volume'], model='multiplicative', period=period)

plt.subplot(4, 1, 3)
plt.plot(result.seasonal, label='Seasonal', color='green')
plt.title('Seasonal Component')
plt.legend()
plt.show()

plt.subplot(4, 1, 2)
plt.plot(result.trend, label='Trend', color='yellow')
plt.title('Trend Component')
plt.legend()
plt.show()

plt.figure(figsize=(12, 6))
plt.subplot(4, 1, 1)
plt.plot(data['Volume'], label='original')
plt.title('Original Time Series')
plt.legend()
plt.show()

```















### OUTPUT:

#### FIRST FIVE ROWS:

![Screenshot 2024-10-16 144806](https://github.com/user-attachments/assets/fd3fb4ef-321c-4391-86de-d6bda997ed2a)





#### PLOTTING THE DATA:
![Screenshot 2024-10-16 143423](https://github.com/user-attachments/assets/e2ce2945-b82c-441f-a5bd-7377b125bcfa)



#### SEASONAL PLOT REPRESENTATION :

![Screenshot 2024-10-16 143534](https://github.com/user-attachments/assets/b93fd138-5f15-41ee-9daf-4d571f0b91e6)





#### TREND PLOT REPRESENTATION :
![Screenshot 2024-10-16 143657](https://github.com/user-attachments/assets/2e0f5dc2-5ac8-4363-becb-df30594b7a58)




#### OVERAL REPRESENTATION:
![Screenshot 2024-10-16 143652](https://github.com/user-attachments/assets/3183f1dc-9818-435c-b436-4f71172b43d7)



### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
