```python
#importing required libraries for the analysis
```


```python
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
```


```python
#loading the file from system onto dataframe variable
```


```python
df = pd.read_csv(r"/Users/gurudarshan/UOG/Projects/project 4/hotel_bookings.csv")
```


```python
type(df)
```




    pandas.core.frame.DataFrame




```python
#.info()provides info of all data in each column
```


```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 119390 entries, 0 to 119389
    Data columns (total 32 columns):
     #   Column                          Non-Null Count   Dtype  
    ---  ------                          --------------   -----  
     0   hotel                           119390 non-null  object 
     1   is_canceled                     119390 non-null  int64  
     2   lead_time                       119390 non-null  int64  
     3   arrival_date_year               119390 non-null  int64  
     4   arrival_date_month              119390 non-null  object 
     5   arrival_date_week_number        119390 non-null  int64  
     6   arrival_date_day_of_month       119390 non-null  int64  
     7   stays_in_weekend_nights         119390 non-null  int64  
     8   stays_in_week_nights            119390 non-null  int64  
     9   adults                          119390 non-null  int64  
     10  children                        119386 non-null  float64
     11  babies                          119390 non-null  int64  
     12  meal                            119390 non-null  object 
     13  country                         118902 non-null  object 
     14  market_segment                  119390 non-null  object 
     15  distribution_channel            119390 non-null  object 
     16  is_repeated_guest               119390 non-null  int64  
     17  previous_cancellations          119390 non-null  int64  
     18  previous_bookings_not_canceled  119390 non-null  int64  
     19  reserved_room_type              119390 non-null  object 
     20  assigned_room_type              119390 non-null  object 
     21  booking_changes                 119390 non-null  int64  
     22  deposit_type                    119390 non-null  object 
     23  agent                           103050 non-null  float64
     24  company                         6797 non-null    float64
     25  days_in_waiting_list            119390 non-null  int64  
     26  customer_type                   119390 non-null  object 
     27  adr                             119390 non-null  float64
     28  required_car_parking_spaces     119390 non-null  int64  
     29  total_of_special_requests       119390 non-null  int64  
     30  reservation_status              119390 non-null  object 
     31  reservation_status_date         119390 non-null  object 
    dtypes: float64(4), int64(16), object(12)
    memory usage: 29.1+ MB



```python
#Provides top 5 rows of the table to provide overview
```


```python
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>hotel</th>
      <th>is_canceled</th>
      <th>lead_time</th>
      <th>arrival_date_year</th>
      <th>arrival_date_month</th>
      <th>arrival_date_week_number</th>
      <th>arrival_date_day_of_month</th>
      <th>stays_in_weekend_nights</th>
      <th>stays_in_week_nights</th>
      <th>adults</th>
      <th>...</th>
      <th>deposit_type</th>
      <th>agent</th>
      <th>company</th>
      <th>days_in_waiting_list</th>
      <th>customer_type</th>
      <th>adr</th>
      <th>required_car_parking_spaces</th>
      <th>total_of_special_requests</th>
      <th>reservation_status</th>
      <th>reservation_status_date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>342</td>
      <td>2015</td>
      <td>July</td>
      <td>27</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>0.0</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>7/1/2015</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>737</td>
      <td>2015</td>
      <td>July</td>
      <td>27</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>0.0</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>7/1/2015</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>7</td>
      <td>2015</td>
      <td>July</td>
      <td>27</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>75.0</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>7/2/2015</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>13</td>
      <td>2015</td>
      <td>July</td>
      <td>27</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>304.0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>75.0</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>7/2/2015</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>14</td>
      <td>2015</td>
      <td>July</td>
      <td>27</td>
      <td>1</td>
      <td>0</td>
      <td>2</td>
      <td>2</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>240.0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>98.0</td>
      <td>0</td>
      <td>1</td>
      <td>Check-Out</td>
      <td>7/3/2015</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 32 columns</p>
</div>




```python
#Provides dimensions of the table (rows , columns)
```


```python
df.shape
```




    (119390, 32)




```python
#Data Cleaning 
#Let's check for duplicated rows
```


```python
df1 = df.drop_duplicates()
```


```python
df1.shape
```




    (87396, 32)




```python
#Reduced number of rows in df1 shows duplicated rows were dropped from the table.
```


```python
df1.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>hotel</th>
      <th>is_canceled</th>
      <th>lead_time</th>
      <th>arrival_date_year</th>
      <th>arrival_date_month</th>
      <th>arrival_date_week_number</th>
      <th>arrival_date_day_of_month</th>
      <th>stays_in_weekend_nights</th>
      <th>stays_in_week_nights</th>
      <th>adults</th>
      <th>...</th>
      <th>deposit_type</th>
      <th>agent</th>
      <th>company</th>
      <th>days_in_waiting_list</th>
      <th>customer_type</th>
      <th>adr</th>
      <th>required_car_parking_spaces</th>
      <th>total_of_special_requests</th>
      <th>reservation_status</th>
      <th>reservation_status_date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>342</td>
      <td>2015</td>
      <td>July</td>
      <td>27</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>0.0</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>7/1/2015</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>737</td>
      <td>2015</td>
      <td>July</td>
      <td>27</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>0.0</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>7/1/2015</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>7</td>
      <td>2015</td>
      <td>July</td>
      <td>27</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>75.0</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>7/2/2015</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>13</td>
      <td>2015</td>
      <td>July</td>
      <td>27</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>304.0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>75.0</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>7/2/2015</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>14</td>
      <td>2015</td>
      <td>July</td>
      <td>27</td>
      <td>1</td>
      <td>0</td>
      <td>2</td>
      <td>2</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>240.0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>98.0</td>
      <td>0</td>
      <td>1</td>
      <td>Check-Out</td>
      <td>7/3/2015</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 32 columns</p>
</div>




```python
df1.columns
```




    Index(['hotel', 'is_canceled', 'lead_time', 'arrival_date_year',
           'arrival_date_month', 'arrival_date_week_number',
           'arrival_date_day_of_month', 'stays_in_weekend_nights',
           'stays_in_week_nights', 'adults', 'children', 'babies', 'meal',
           'country', 'market_segment', 'distribution_channel',
           'is_repeated_guest', 'previous_cancellations',
           'previous_bookings_not_canceled', 'reserved_room_type',
           'assigned_room_type', 'booking_changes', 'deposit_type', 'agent',
           'company', 'days_in_waiting_list', 'customer_type', 'adr',
           'required_car_parking_spaces', 'total_of_special_requests',
           'reservation_status', 'reservation_status_date'],
          dtype='object')




```python
#No booking should have no. of adults + no. of children + no. of babies as 0
#considering these rows as invalid booking
#Filtering these rows from data
```


```python
filter =  (df1['children']==0) & (df1['adults']==0) & (df1['babies']==0)
```


```python
df1[filter]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>hotel</th>
      <th>is_canceled</th>
      <th>lead_time</th>
      <th>arrival_date_year</th>
      <th>arrival_date_month</th>
      <th>arrival_date_week_number</th>
      <th>arrival_date_day_of_month</th>
      <th>stays_in_weekend_nights</th>
      <th>stays_in_week_nights</th>
      <th>adults</th>
      <th>...</th>
      <th>deposit_type</th>
      <th>agent</th>
      <th>company</th>
      <th>days_in_waiting_list</th>
      <th>customer_type</th>
      <th>adr</th>
      <th>required_car_parking_spaces</th>
      <th>total_of_special_requests</th>
      <th>reservation_status</th>
      <th>reservation_status_date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2224</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>1</td>
      <td>2015</td>
      <td>October</td>
      <td>41</td>
      <td>6</td>
      <td>0</td>
      <td>3</td>
      <td>0</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>NaN</td>
      <td>174.0</td>
      <td>0</td>
      <td>Transient-Party</td>
      <td>0.00</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>10/6/2015</td>
    </tr>
    <tr>
      <th>2409</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>0</td>
      <td>2015</td>
      <td>October</td>
      <td>42</td>
      <td>12</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>NaN</td>
      <td>174.0</td>
      <td>0</td>
      <td>Transient</td>
      <td>0.00</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>10/12/2015</td>
    </tr>
    <tr>
      <th>3181</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>36</td>
      <td>2015</td>
      <td>November</td>
      <td>47</td>
      <td>20</td>
      <td>1</td>
      <td>2</td>
      <td>0</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>38.0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient-Party</td>
      <td>0.00</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>11/23/2015</td>
    </tr>
    <tr>
      <th>3684</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>165</td>
      <td>2015</td>
      <td>December</td>
      <td>53</td>
      <td>30</td>
      <td>1</td>
      <td>4</td>
      <td>0</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>308.0</td>
      <td>NaN</td>
      <td>122</td>
      <td>Transient-Party</td>
      <td>0.00</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>1/4/2016</td>
    </tr>
    <tr>
      <th>3708</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>165</td>
      <td>2015</td>
      <td>December</td>
      <td>53</td>
      <td>30</td>
      <td>2</td>
      <td>4</td>
      <td>0</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>308.0</td>
      <td>NaN</td>
      <td>122</td>
      <td>Transient-Party</td>
      <td>0.00</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>1/5/2016</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>115029</th>
      <td>City Hotel</td>
      <td>0</td>
      <td>107</td>
      <td>2017</td>
      <td>June</td>
      <td>26</td>
      <td>27</td>
      <td>0</td>
      <td>3</td>
      <td>0</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>7.0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>100.80</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>6/30/2017</td>
    </tr>
    <tr>
      <th>115091</th>
      <td>City Hotel</td>
      <td>0</td>
      <td>1</td>
      <td>2017</td>
      <td>June</td>
      <td>26</td>
      <td>30</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>0.00</td>
      <td>1</td>
      <td>1</td>
      <td>Check-Out</td>
      <td>7/1/2017</td>
    </tr>
    <tr>
      <th>116251</th>
      <td>City Hotel</td>
      <td>0</td>
      <td>44</td>
      <td>2017</td>
      <td>July</td>
      <td>28</td>
      <td>15</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>425.0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>73.80</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>7/17/2017</td>
    </tr>
    <tr>
      <th>116534</th>
      <td>City Hotel</td>
      <td>0</td>
      <td>2</td>
      <td>2017</td>
      <td>July</td>
      <td>28</td>
      <td>15</td>
      <td>2</td>
      <td>5</td>
      <td>0</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>9.0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient-Party</td>
      <td>22.86</td>
      <td>0</td>
      <td>1</td>
      <td>Check-Out</td>
      <td>7/22/2017</td>
    </tr>
    <tr>
      <th>117087</th>
      <td>City Hotel</td>
      <td>0</td>
      <td>170</td>
      <td>2017</td>
      <td>July</td>
      <td>30</td>
      <td>27</td>
      <td>0</td>
      <td>2</td>
      <td>0</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>52.0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>0.00</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>7/29/2017</td>
    </tr>
  </tbody>
</table>
<p>166 rows × 32 columns</p>
</div>




```python

```


```python
df1[filter].shape
```




    (166, 32)




```python
df1[~filter].shape
```




    (87230, 32)




```python
#We can see that 166 rows have values where all three colmns adults,children and babies are 0
```


```python
df2 = df1[~filter]
```


```python
df2.shape
```




    (87230, 32)




```python
#Performing descriptive analysis
```


```python
df.columns
```




    Index(['hotel', 'is_canceled', 'lead_time', 'arrival_date_year',
           'arrival_date_month', 'arrival_date_week_number',
           'arrival_date_day_of_month', 'stays_in_weekend_nights',
           'stays_in_week_nights', 'adults', 'children', 'babies', 'meal',
           'country', 'market_segment', 'distribution_channel',
           'is_repeated_guest', 'previous_cancellations',
           'previous_bookings_not_canceled', 'reserved_room_type',
           'assigned_room_type', 'booking_changes', 'deposit_type', 'agent',
           'company', 'days_in_waiting_list', 'customer_type', 'adr',
           'required_car_parking_spaces', 'total_of_special_requests',
           'reservation_status', 'reservation_status_date'],
          dtype='object')




```python
df2[['lead_time' , 'total_of_special_requests' , 'adr']].describe()

## getting (mean, median , std , percentile) of above features
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>lead_time</th>
      <th>total_of_special_requests</th>
      <th>adr</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>87230.000000</td>
      <td>87230.000000</td>
      <td>87230.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>79.971019</td>
      <td>0.698934</td>
      <td>106.518031</td>
    </tr>
    <tr>
      <th>std</th>
      <td>86.058683</td>
      <td>0.832051</td>
      <td>54.891227</td>
    </tr>
    <tr>
      <th>min</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>-6.380000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>11.000000</td>
      <td>0.000000</td>
      <td>72.250000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>49.000000</td>
      <td>0.000000</td>
      <td>98.200000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>125.000000</td>
      <td>1.000000</td>
      <td>134.100000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>737.000000</td>
      <td>5.000000</td>
      <td>5400.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2[['lead_time' , 'total_of_special_requests' , 'adr']].describe().T

## getting (mean, median , std , percentile) of above features
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>count</th>
      <th>mean</th>
      <th>std</th>
      <th>min</th>
      <th>25%</th>
      <th>50%</th>
      <th>75%</th>
      <th>max</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>lead_time</th>
      <td>87230.0</td>
      <td>79.971019</td>
      <td>86.058683</td>
      <td>0.00</td>
      <td>11.00</td>
      <td>49.0</td>
      <td>125.0</td>
      <td>737.0</td>
    </tr>
    <tr>
      <th>total_of_special_requests</th>
      <td>87230.0</td>
      <td>0.698934</td>
      <td>0.832051</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>adr</th>
      <td>87230.0</td>
      <td>106.518031</td>
      <td>54.891227</td>
      <td>-6.38</td>
      <td>72.25</td>
      <td>98.2</td>
      <td>134.1</td>
      <td>5400.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
import numpy as np

for col in ['lead_time', 'total_of_special_requests', 'adr']:
    print('feature name : {}'.format(col))
    
    for i in range(90, 101, 1):
        quantile_value = np.quantile(df2[col], q=i/100)  # Use i/100 to get the desired percentile
        print('{}th quantile value is {}'.format(i, quantile_value))
    print('\n')

```

    feature name : lead_time
    90th quantile value is 204.0
    91th quantile value is 212.0
    92th quantile value is 220.0
    93th quantile value is 230.0
    94th quantile value is 241.0
    95th quantile value is 256.0
    96th quantile value is 272.0
    97th quantile value is 291.0
    98th quantile value is 315.0
    99th quantile value is 347.0
    100th quantile value is 737.0
    
    
    feature name : total_of_special_requests
    90th quantile value is 2.0
    91th quantile value is 2.0
    92th quantile value is 2.0
    93th quantile value is 2.0
    94th quantile value is 2.0
    95th quantile value is 2.0
    96th quantile value is 2.0
    97th quantile value is 3.0
    98th quantile value is 3.0
    99th quantile value is 3.0
    100th quantile value is 5.0
    
    
    feature name : adr
    90th quantile value is 174.0
    91th quantile value is 179.0
    92th quantile value is 185.0
    93th quantile value is 190.0
    94th quantile value is 197.1
    95th quantile value is 204.13300000000018
    96th quantile value is 213.0
    97th quantile value is 225.0
    98th quantile value is 239.0
    99th quantile value is 261.6207000000011
    100th quantile value is 5400.0
    
    



```python
#"adr" feature seems to have Outlier as 99th percentile value is 261 but 100th percentile(max value) is 5400 .. 
```


```python
#SPATIAL ANALYSIS
```


```python
df2.columns
```




    Index(['hotel', 'is_canceled', 'lead_time', 'arrival_date_year',
           'arrival_date_month', 'arrival_date_week_number',
           'arrival_date_day_of_month', 'stays_in_weekend_nights',
           'stays_in_week_nights', 'adults', 'children', 'babies', 'meal',
           'country', 'market_segment', 'distribution_channel',
           'is_repeated_guest', 'previous_cancellations',
           'previous_bookings_not_canceled', 'reserved_room_type',
           'assigned_room_type', 'booking_changes', 'deposit_type', 'agent',
           'company', 'days_in_waiting_list', 'customer_type', 'adr',
           'required_car_parking_spaces', 'total_of_special_requests',
           'reservation_status', 'reservation_status_date'],
          dtype='object')




```python
not_cancelled = df2[df2['is_canceled']==0]
```


```python
not_cancelled
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>hotel</th>
      <th>is_canceled</th>
      <th>lead_time</th>
      <th>arrival_date_year</th>
      <th>arrival_date_month</th>
      <th>arrival_date_week_number</th>
      <th>arrival_date_day_of_month</th>
      <th>stays_in_weekend_nights</th>
      <th>stays_in_week_nights</th>
      <th>adults</th>
      <th>...</th>
      <th>deposit_type</th>
      <th>agent</th>
      <th>company</th>
      <th>days_in_waiting_list</th>
      <th>customer_type</th>
      <th>adr</th>
      <th>required_car_parking_spaces</th>
      <th>total_of_special_requests</th>
      <th>reservation_status</th>
      <th>reservation_status_date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>342</td>
      <td>2015</td>
      <td>July</td>
      <td>27</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>0.00</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>7/1/2015</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>737</td>
      <td>2015</td>
      <td>July</td>
      <td>27</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>0.00</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>7/1/2015</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>7</td>
      <td>2015</td>
      <td>July</td>
      <td>27</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>75.00</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>7/2/2015</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>13</td>
      <td>2015</td>
      <td>July</td>
      <td>27</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>304.0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>75.00</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>7/2/2015</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>14</td>
      <td>2015</td>
      <td>July</td>
      <td>27</td>
      <td>1</td>
      <td>0</td>
      <td>2</td>
      <td>2</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>240.0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>98.00</td>
      <td>0</td>
      <td>1</td>
      <td>Check-Out</td>
      <td>7/3/2015</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>119385</th>
      <td>City Hotel</td>
      <td>0</td>
      <td>23</td>
      <td>2017</td>
      <td>August</td>
      <td>35</td>
      <td>30</td>
      <td>2</td>
      <td>5</td>
      <td>2</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>394.0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>96.14</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>9/6/2017</td>
    </tr>
    <tr>
      <th>119386</th>
      <td>City Hotel</td>
      <td>0</td>
      <td>102</td>
      <td>2017</td>
      <td>August</td>
      <td>35</td>
      <td>31</td>
      <td>2</td>
      <td>5</td>
      <td>3</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>9.0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>225.43</td>
      <td>0</td>
      <td>2</td>
      <td>Check-Out</td>
      <td>9/7/2017</td>
    </tr>
    <tr>
      <th>119387</th>
      <td>City Hotel</td>
      <td>0</td>
      <td>34</td>
      <td>2017</td>
      <td>August</td>
      <td>35</td>
      <td>31</td>
      <td>2</td>
      <td>5</td>
      <td>2</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>9.0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>157.71</td>
      <td>0</td>
      <td>4</td>
      <td>Check-Out</td>
      <td>9/7/2017</td>
    </tr>
    <tr>
      <th>119388</th>
      <td>City Hotel</td>
      <td>0</td>
      <td>109</td>
      <td>2017</td>
      <td>August</td>
      <td>35</td>
      <td>31</td>
      <td>2</td>
      <td>5</td>
      <td>2</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>89.0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>104.40</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>9/7/2017</td>
    </tr>
    <tr>
      <th>119389</th>
      <td>City Hotel</td>
      <td>0</td>
      <td>205</td>
      <td>2017</td>
      <td>August</td>
      <td>35</td>
      <td>29</td>
      <td>2</td>
      <td>7</td>
      <td>2</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>9.0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>151.20</td>
      <td>0</td>
      <td>2</td>
      <td>Check-Out</td>
      <td>9/7/2017</td>
    </tr>
  </tbody>
</table>
<p>63221 rows × 32 columns</p>
</div>




```python
country = not_cancelled['country'].value_counts().reset_index()
```


```python
country
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>index</th>
      <th>country</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>PRT</td>
      <td>17573</td>
    </tr>
    <tr>
      <th>1</th>
      <td>GBR</td>
      <td>8440</td>
    </tr>
    <tr>
      <th>2</th>
      <td>FRA</td>
      <td>7091</td>
    </tr>
    <tr>
      <th>3</th>
      <td>ESP</td>
      <td>5382</td>
    </tr>
    <tr>
      <th>4</th>
      <td>DEU</td>
      <td>4332</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>160</th>
      <td>ZMB</td>
      <td>1</td>
    </tr>
    <tr>
      <th>161</th>
      <td>SYC</td>
      <td>1</td>
    </tr>
    <tr>
      <th>162</th>
      <td>MDG</td>
      <td>1</td>
    </tr>
    <tr>
      <th>163</th>
      <td>SMR</td>
      <td>1</td>
    </tr>
    <tr>
      <th>164</th>
      <td>FRO</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
<p>165 rows × 2 columns</p>
</div>




```python
country.columns = ['country','No. of guests']
```


```python
country
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>country</th>
      <th>No. of guests</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>PRT</td>
      <td>17573</td>
    </tr>
    <tr>
      <th>1</th>
      <td>GBR</td>
      <td>8440</td>
    </tr>
    <tr>
      <th>2</th>
      <td>FRA</td>
      <td>7091</td>
    </tr>
    <tr>
      <th>3</th>
      <td>ESP</td>
      <td>5382</td>
    </tr>
    <tr>
      <th>4</th>
      <td>DEU</td>
      <td>4332</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>160</th>
      <td>ZMB</td>
      <td>1</td>
    </tr>
    <tr>
      <th>161</th>
      <td>SYC</td>
      <td>1</td>
    </tr>
    <tr>
      <th>162</th>
      <td>MDG</td>
      <td>1</td>
    </tr>
    <tr>
      <th>163</th>
      <td>SMR</td>
      <td>1</td>
    </tr>
    <tr>
      <th>164</th>
      <td>FRO</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
<p>165 rows × 2 columns</p>
</div>




```python
!pip install chart-studio
!pip install plotly
```

    Requirement already satisfied: chart-studio in /Library/Frameworks/Python.framework/Versions/3.11/lib/python3.11/site-packages (1.1.0)
    Requirement already satisfied: plotly in /Library/Frameworks/Python.framework/Versions/3.11/lib/python3.11/site-packages (from chart-studio) (5.18.0)
    Requirement already satisfied: requests in /Library/Frameworks/Python.framework/Versions/3.11/lib/python3.11/site-packages (from chart-studio) (2.28.2)
    Requirement already satisfied: retrying>=1.3.3 in /Library/Frameworks/Python.framework/Versions/3.11/lib/python3.11/site-packages (from chart-studio) (1.3.4)
    Requirement already satisfied: six in /Library/Frameworks/Python.framework/Versions/3.11/lib/python3.11/site-packages (from chart-studio) (1.16.0)
    Requirement already satisfied: tenacity>=6.2.0 in /Library/Frameworks/Python.framework/Versions/3.11/lib/python3.11/site-packages (from plotly->chart-studio) (8.2.3)
    Requirement already satisfied: packaging in /Library/Frameworks/Python.framework/Versions/3.11/lib/python3.11/site-packages (from plotly->chart-studio) (23.0)
    Requirement already satisfied: charset-normalizer<4,>=2 in /Library/Frameworks/Python.framework/Versions/3.11/lib/python3.11/site-packages (from requests->chart-studio) (3.1.0)
    Requirement already satisfied: idna<4,>=2.5 in /Library/Frameworks/Python.framework/Versions/3.11/lib/python3.11/site-packages (from requests->chart-studio) (3.4)
    Requirement already satisfied: urllib3<1.27,>=1.21.1 in /Library/Frameworks/Python.framework/Versions/3.11/lib/python3.11/site-packages (from requests->chart-studio) (1.26.15)
    Requirement already satisfied: certifi>=2017.4.17 in /Library/Frameworks/Python.framework/Versions/3.11/lib/python3.11/site-packages (from requests->chart-studio) (2022.12.7)
    
    [1m[[0m[34;49mnotice[0m[1;39;49m][0m[39;49m A new release of pip is available: [0m[31;49m23.2.1[0m[39;49m -> [0m[32;49m23.3.1[0m
    [1m[[0m[34;49mnotice[0m[1;39;49m][0m[39;49m To update, run: [0m[32;49mpip install --upgrade pip[0m
    Requirement already satisfied: plotly in /Library/Frameworks/Python.framework/Versions/3.11/lib/python3.11/site-packages (5.18.0)
    Requirement already satisfied: tenacity>=6.2.0 in /Library/Frameworks/Python.framework/Versions/3.11/lib/python3.11/site-packages (from plotly) (8.2.3)
    Requirement already satisfied: packaging in /Library/Frameworks/Python.framework/Versions/3.11/lib/python3.11/site-packages (from plotly) (23.0)
    
    [1m[[0m[34;49mnotice[0m[1;39;49m][0m[39;49m A new release of pip is available: [0m[31;49m23.2.1[0m[39;49m -> [0m[32;49m23.3.1[0m
    [1m[[0m[34;49mnotice[0m[1;39;49m][0m[39;49m To update, run: [0m[32;49mpip install --upgrade pip[0m



```python
### establishing the entire set-up of Plotly..

import chart_studio.plotly as py
## chart_studio provides a web-service for hosting graphs!

import plotly.graph_objs as go
import plotly.express as px

from plotly.offline import download_plotlyjs , init_notebook_mode , plot , iplot

## iplot() when working in a Jupyter Notebook to
## display the plot in the Ipython notebook.

init_notebook_mode(connected=True)
```


<script type="text/javascript">
window.PlotlyConfig = {MathJaxConfig: 'local'};
if (window.MathJax && window.MathJax.Hub && window.MathJax.Hub.Config) {window.MathJax.Hub.Config({SVG: {font: "STIX-Web"}});}
if (typeof require !== 'undefined') {
require.undef("plotly");
requirejs.config({
    paths: {
        'plotly': ['https://cdn.plot.ly/plotly-2.12.1.min']
    }
});
require(['plotly'], function(Plotly) {
    window._Plotly = Plotly;
});
}
</script>




```python
# show on map

map_guest = px.choropleth(data_frame = country , 
              locations= country['country'] , 
              color=country['No. of guests'] , 
              hover_name=country['country'] , 
              title= "Home country of Guests"
          
             )
```


```python
map_guest.show()
```


<div>                            <div id="d453bddd-4d62-4661-8cb3-8cd092300325" class="plotly-graph-div" style="height:525px; width:100%;"></div>            <script type="text/javascript">                require(["plotly"], function(Plotly) {                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("d453bddd-4d62-4661-8cb3-8cd092300325")) {                    Plotly.newPlot(                        "d453bddd-4d62-4661-8cb3-8cd092300325",                        [{"coloraxis":"coloraxis","geo":"geo","hovertemplate":"<b>%{hovertext}</b><br><br>country=%{location}<br>No. of guests=%{z}<extra></extra>","hovertext":["PRT","GBR","FRA","ESP","DEU","IRL","ITA","BEL","NLD","USA","BRA","CHE","CN","AUT","SWE","POL","CHN","NOR","FIN","ROU","RUS","DNK","AUS","ISR","JPN","LUX","ARG","AGO","HUN","MAR","TUR","IND","CZE","GRC","KOR","HRV","LTU","MEX","DZA","EST","NZL","BGR","IRN","SRB","ZAF","CHL","COL","LVA","UKR","MOZ","SVK","CYP","SVN","TWN","THA","ISL","LBN","SGP","EGY","URY","MYS","PER","TUN","ECU","CRI","JOR","BLR","SAU","KAZ","OMN","PHL","NGA","VEN","MLT","IDN","IRQ","CPV","CMR","PRI","KWT","ALB","BIH","PAN","LBY","GNB","AZE","CUB","MKD","ARE","VNM","JAM","LKA","ARM","MUS","DOM","CAF","PAK","GEO","SUR","KEN","PRY","QAT","CIV","GIB","MDV","MNE","SEN","SYR","MCO","GTM","BGD","BOL","ATA","TZA","ABW","TMP","GAB","SLV","GHA","LAO","BRB","LIE","RWA","STP","ETH","UGA","COM","HKG","KNA","ZWE","TGO","MWI","AND","UZB","LCA","BWA","BDI","MRT","ASM","PYF","NCL","KIR","SDN","ATF","TJK","SLE","GUY","AIA","PLW","NPL","MMR","DJI","BFA","CYM","MAC","BHS","MLI","DMA","BHR","NAM","ZMB","SYC","MDG","SMR","FRO"],"locations":["PRT","GBR","FRA","ESP","DEU","IRL","ITA","BEL","NLD","USA","BRA","CHE","CN","AUT","SWE","POL","CHN","NOR","FIN","ROU","RUS","DNK","AUS","ISR","JPN","LUX","ARG","AGO","HUN","MAR","TUR","IND","CZE","GRC","KOR","HRV","LTU","MEX","DZA","EST","NZL","BGR","IRN","SRB","ZAF","CHL","COL","LVA","UKR","MOZ","SVK","CYP","SVN","TWN","THA","ISL","LBN","SGP","EGY","URY","MYS","PER","TUN","ECU","CRI","JOR","BLR","SAU","KAZ","OMN","PHL","NGA","VEN","MLT","IDN","IRQ","CPV","CMR","PRI","KWT","ALB","BIH","PAN","LBY","GNB","AZE","CUB","MKD","ARE","VNM","JAM","LKA","ARM","MUS","DOM","CAF","PAK","GEO","SUR","KEN","PRY","QAT","CIV","GIB","MDV","MNE","SEN","SYR","MCO","GTM","BGD","BOL","ATA","TZA","ABW","TMP","GAB","SLV","GHA","LAO","BRB","LIE","RWA","STP","ETH","UGA","COM","HKG","KNA","ZWE","TGO","MWI","AND","UZB","LCA","BWA","BDI","MRT","ASM","PYF","NCL","KIR","SDN","ATF","TJK","SLE","GUY","AIA","PLW","NPL","MMR","DJI","BFA","CYM","MAC","BHS","MLI","DMA","BHR","NAM","ZMB","SYC","MDG","SMR","FRO"],"name":"","z":[17573,8440,7091,5382,4332,2347,1986,1670,1560,1412,1266,1182,868,777,656,600,424,370,357,340,337,293,286,270,158,158,152,149,137,128,116,108,103,84,76,68,66,65,61,61,59,59,57,51,49,49,46,43,42,39,38,36,34,30,24,22,22,21,21,21,21,20,19,18,17,16,16,15,14,14,13,13,13,12,11,11,11,10,10,10,9,9,8,8,8,8,8,7,7,6,6,6,6,6,6,5,5,5,5,4,4,4,4,4,3,3,3,3,3,3,3,3,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1],"type":"choropleth"}],                        {"template":{"data":{"histogram2dcontour":[{"type":"histogram2dcontour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"choropleth":[{"type":"choropleth","colorbar":{"outlinewidth":0,"ticks":""}}],"histogram2d":[{"type":"histogram2d","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmap":[{"type":"heatmap","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmapgl":[{"type":"heatmapgl","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"contourcarpet":[{"type":"contourcarpet","colorbar":{"outlinewidth":0,"ticks":""}}],"contour":[{"type":"contour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"surface":[{"type":"surface","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"mesh3d":[{"type":"mesh3d","colorbar":{"outlinewidth":0,"ticks":""}}],"scatter":[{"fillpattern":{"fillmode":"overlay","size":10,"solidity":0.2},"type":"scatter"}],"parcoords":[{"type":"parcoords","line":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolargl":[{"type":"scatterpolargl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"bar":[{"error_x":{"color":"#2a3f5f"},"error_y":{"color":"#2a3f5f"},"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"scattergeo":[{"type":"scattergeo","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolar":[{"type":"scatterpolar","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"scattergl":[{"type":"scattergl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatter3d":[{"type":"scatter3d","line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattermapbox":[{"type":"scattermapbox","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterternary":[{"type":"scatterternary","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattercarpet":[{"type":"scattercarpet","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"carpet":[{"aaxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"baxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"type":"carpet"}],"table":[{"cells":{"fill":{"color":"#EBF0F8"},"line":{"color":"white"}},"header":{"fill":{"color":"#C8D4E3"},"line":{"color":"white"}},"type":"table"}],"barpolar":[{"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"pie":[{"automargin":true,"type":"pie"}]},"layout":{"autotypenumbers":"strict","colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#2a3f5f"},"hovermode":"closest","hoverlabel":{"align":"left"},"paper_bgcolor":"white","plot_bgcolor":"#E5ECF6","polar":{"bgcolor":"#E5ECF6","angularaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"radialaxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"ternary":{"bgcolor":"#E5ECF6","aaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"baxis":{"gridcolor":"white","linecolor":"white","ticks":""},"caxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]]},"xaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"yaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"scene":{"xaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"yaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"zaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2}},"shapedefaults":{"line":{"color":"#2a3f5f"}},"annotationdefaults":{"arrowcolor":"#2a3f5f","arrowhead":0,"arrowwidth":1},"geo":{"bgcolor":"white","landcolor":"#E5ECF6","subunitcolor":"white","showland":true,"showlakes":true,"lakecolor":"white"},"title":{"x":0.05},"mapbox":{"style":"light"}}},"geo":{"domain":{"x":[0.0,1.0],"y":[0.0,1.0]},"center":{}},"coloraxis":{"colorbar":{"title":{"text":"No. of guests"}},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]},"legend":{"tracegroupgap":0},"title":{"text":"Home country of Guests"}},                        {"responsive": true}                    ).then(function(){

var gd = document.getElementById('d453bddd-4d62-4661-8cb3-8cd092300325');
var x = new MutationObserver(function (mutations, observer) {{
        var display = window.getComputedStyle(gd).display;
        if (!display || display === 'none') {{
            console.log([gd, 'removed!']);
            Plotly.purge(gd);
            observer.disconnect();
        }}
}});

// Listen for the removal of the full notebook cells
var notebookContainer = gd.closest('#notebook-container');
if (notebookContainer) &#123;&#123;
    x.observe(notebookContainer, {childList: true});
}}

// Listen for the clearing of the current output cell
var outputEl = gd.closest('.output');
if (outputEl) {{
    x.observe(outputEl, {childList: true});
}}

                        })                };                });            </script>        </div>



```python
#Bookings wrt market segment 
```


```python
df2.columns
```




    Index(['hotel', 'is_canceled', 'lead_time', 'arrival_date_year',
           'arrival_date_month', 'arrival_date_week_number',
           'arrival_date_day_of_month', 'stays_in_weekend_nights',
           'stays_in_week_nights', 'adults', 'children', 'babies', 'meal',
           'country', 'market_segment', 'distribution_channel',
           'is_repeated_guest', 'previous_cancellations',
           'previous_bookings_not_canceled', 'reserved_room_type',
           'assigned_room_type', 'booking_changes', 'deposit_type', 'agent',
           'company', 'days_in_waiting_list', 'customer_type', 'adr',
           'required_car_parking_spaces', 'total_of_special_requests',
           'reservation_status', 'reservation_status_date'],
          dtype='object')




```python
df2['market_segment'].value_counts().values
```




    array([51553, 13855, 11780,  4922,  4200,   692,   226,     2])




```python
df2['market_segment'].value_counts().index
```




    Index(['Online TA', 'Offline TA/TO', 'Direct', 'Groups', 'Corporate',
           'Complementary', 'Aviation', 'Undefined'],
          dtype='object')




```python
# pie plot

fig = px.pie(df2 , 
      values = df2['market_segment'].value_counts().values , 
      names = df2['market_segment'].value_counts().index)
```


```python
fig.show()
```


<div>                            <div id="650425e3-009b-4b70-84a6-161a6ec537e5" class="plotly-graph-div" style="height:525px; width:100%;"></div>            <script type="text/javascript">                require(["plotly"], function(Plotly) {                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("650425e3-009b-4b70-84a6-161a6ec537e5")) {                    Plotly.newPlot(                        "650425e3-009b-4b70-84a6-161a6ec537e5",                        [{"domain":{"x":[0.0,1.0],"y":[0.0,1.0]},"hovertemplate":"label=%{label}<br>value=%{value}<extra></extra>","labels":["Online TA","Offline TA/TO","Direct","Groups","Corporate","Complementary","Aviation","Undefined"],"legendgroup":"","name":"","showlegend":true,"values":[51553,13855,11780,4922,4200,692,226,2],"type":"pie"}],                        {"template":{"data":{"histogram2dcontour":[{"type":"histogram2dcontour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"choropleth":[{"type":"choropleth","colorbar":{"outlinewidth":0,"ticks":""}}],"histogram2d":[{"type":"histogram2d","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmap":[{"type":"heatmap","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmapgl":[{"type":"heatmapgl","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"contourcarpet":[{"type":"contourcarpet","colorbar":{"outlinewidth":0,"ticks":""}}],"contour":[{"type":"contour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"surface":[{"type":"surface","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"mesh3d":[{"type":"mesh3d","colorbar":{"outlinewidth":0,"ticks":""}}],"scatter":[{"fillpattern":{"fillmode":"overlay","size":10,"solidity":0.2},"type":"scatter"}],"parcoords":[{"type":"parcoords","line":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolargl":[{"type":"scatterpolargl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"bar":[{"error_x":{"color":"#2a3f5f"},"error_y":{"color":"#2a3f5f"},"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"scattergeo":[{"type":"scattergeo","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolar":[{"type":"scatterpolar","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"scattergl":[{"type":"scattergl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatter3d":[{"type":"scatter3d","line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattermapbox":[{"type":"scattermapbox","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterternary":[{"type":"scatterternary","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattercarpet":[{"type":"scattercarpet","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"carpet":[{"aaxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"baxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"type":"carpet"}],"table":[{"cells":{"fill":{"color":"#EBF0F8"},"line":{"color":"white"}},"header":{"fill":{"color":"#C8D4E3"},"line":{"color":"white"}},"type":"table"}],"barpolar":[{"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"pie":[{"automargin":true,"type":"pie"}]},"layout":{"autotypenumbers":"strict","colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#2a3f5f"},"hovermode":"closest","hoverlabel":{"align":"left"},"paper_bgcolor":"white","plot_bgcolor":"#E5ECF6","polar":{"bgcolor":"#E5ECF6","angularaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"radialaxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"ternary":{"bgcolor":"#E5ECF6","aaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"baxis":{"gridcolor":"white","linecolor":"white","ticks":""},"caxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]]},"xaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"yaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"scene":{"xaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"yaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"zaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2}},"shapedefaults":{"line":{"color":"#2a3f5f"}},"annotationdefaults":{"arrowcolor":"#2a3f5f","arrowhead":0,"arrowwidth":1},"geo":{"bgcolor":"white","landcolor":"#E5ECF6","subunitcolor":"white","showland":true,"showlakes":true,"lakecolor":"white"},"title":{"x":0.05},"mapbox":{"style":"light"}}},"legend":{"tracegroupgap":0},"margin":{"t":60}},                        {"responsive": true}                    ).then(function(){

var gd = document.getElementById('650425e3-009b-4b70-84a6-161a6ec537e5');
var x = new MutationObserver(function (mutations, observer) {{
        var display = window.getComputedStyle(gd).display;
        if (!display || display === 'none') {{
            console.log([gd, 'removed!']);
            Plotly.purge(gd);
            observer.disconnect();
        }}
}});

// Listen for the removal of the full notebook cells
var notebookContainer = gd.closest('#notebook-container');
if (notebookContainer) {{
    x.observe(notebookContainer, {childList: true});
}}

// Listen for the clearing of the current output cell
var outputEl = gd.closest('.output');
if (outputEl) {{
    x.observe(outputEl, {childList: true});
}}

                        })                };                });            </script>        </div>



```python
## 7.. Total guests arrival on each day : 

```


```python
df2.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>hotel</th>
      <th>is_canceled</th>
      <th>lead_time</th>
      <th>arrival_date_year</th>
      <th>arrival_date_month</th>
      <th>arrival_date_week_number</th>
      <th>arrival_date_day_of_month</th>
      <th>stays_in_weekend_nights</th>
      <th>stays_in_week_nights</th>
      <th>adults</th>
      <th>...</th>
      <th>deposit_type</th>
      <th>agent</th>
      <th>company</th>
      <th>days_in_waiting_list</th>
      <th>customer_type</th>
      <th>adr</th>
      <th>required_car_parking_spaces</th>
      <th>total_of_special_requests</th>
      <th>reservation_status</th>
      <th>reservation_status_date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>342</td>
      <td>2015</td>
      <td>July</td>
      <td>27</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>0.0</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>7/1/2015</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>737</td>
      <td>2015</td>
      <td>July</td>
      <td>27</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>0.0</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>7/1/2015</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>7</td>
      <td>2015</td>
      <td>July</td>
      <td>27</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>75.0</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>7/2/2015</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>13</td>
      <td>2015</td>
      <td>July</td>
      <td>27</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>304.0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>75.0</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>7/2/2015</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>14</td>
      <td>2015</td>
      <td>July</td>
      <td>27</td>
      <td>1</td>
      <td>0</td>
      <td>2</td>
      <td>2</td>
      <td>...</td>
      <td>No Deposit</td>
      <td>240.0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>98.0</td>
      <td>0</td>
      <td>1</td>
      <td>Check-Out</td>
      <td>7/3/2015</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 32 columns</p>
</div>




```python
df2.columns
```




    Index(['hotel', 'is_canceled', 'lead_time', 'arrival_date_year',
           'arrival_date_month', 'arrival_date_week_number',
           'arrival_date_day_of_month', 'stays_in_weekend_nights',
           'stays_in_week_nights', 'adults', 'children', 'babies', 'meal',
           'country', 'market_segment', 'distribution_channel',
           'is_repeated_guest', 'previous_cancellations',
           'previous_bookings_not_canceled', 'reserved_room_type',
           'assigned_room_type', 'booking_changes', 'deposit_type', 'agent',
           'company', 'days_in_waiting_list', 'customer_type', 'adr',
           'required_car_parking_spaces', 'total_of_special_requests',
           'reservation_status', 'reservation_status_date'],
          dtype='object')




```python
#Convert 'arrival_date_month' to index value for date format
#Using dictionary to assign value to each month
```


```python
df2.values
```




    array([['Resort Hotel', 0, 342, ..., 0, 'Check-Out', '7/1/2015'],
           ['Resort Hotel', 0, 737, ..., 0, 'Check-Out', '7/1/2015'],
           ['Resort Hotel', 0, 7, ..., 0, 'Check-Out', '7/2/2015'],
           ...,
           ['City Hotel', 0, 34, ..., 4, 'Check-Out', '9/7/2017'],
           ['City Hotel', 0, 109, ..., 0, 'Check-Out', '9/7/2017'],
           ['City Hotel', 0, 205, ..., 2, 'Check-Out', '9/7/2017']],
          dtype=object)




```python
df2['arrival_date_month'].unique()
```




    array(['July', 'August', 'September', 'October', 'November', 'December',
           'January', 'February', 'March', 'April', 'May', 'June'],
          dtype=object)




```python
dict_month = {'July':7, 'August':8, 'September':9, 'October':10, 'November':11, 'December':12,
       'January':1, 'February':2, 'March':3, 'April':4, 'May':5, 'June':6}
```


```python
dict_month
```




    {'July': 7,
     'August': 8,
     'September': 9,
     'October': 10,
     'November': 11,
     'December': 12,
     'January': 1,
     'February': 2,
     'March': 3,
     'April': 4,
     'May': 5,
     'June': 6}




```python
df2['arrival_date_month_index'] = df2['arrival_date_month'].map(dict_month)
```

    /var/folders/sy/gwh3by9524761shnjb3l2fnh0000gp/T/ipykernel_73352/1994572841.py:1: SettingWithCopyWarning:
    
    
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
    



```python
import warnings
from warnings import filterwarnings
filterwarnings('ignore')
```


```python
df2.columns
```




    Index(['hotel', 'is_canceled', 'lead_time', 'arrival_date_year',
           'arrival_date_month', 'arrival_date_week_number',
           'arrival_date_day_of_month', 'stays_in_weekend_nights',
           'stays_in_week_nights', 'adults', 'children', 'babies', 'meal',
           'country', 'market_segment', 'distribution_channel',
           'is_repeated_guest', 'previous_cancellations',
           'previous_bookings_not_canceled', 'reserved_room_type',
           'assigned_room_type', 'booking_changes', 'deposit_type', 'agent',
           'company', 'days_in_waiting_list', 'customer_type', 'adr',
           'required_car_parking_spaces', 'total_of_special_requests',
           'reservation_status', 'reservation_status_date',
           'arrival_date_month_index'],
          dtype='object')




```python
df2[['arrival_date_year',
       'arrival_date_month_index' , 'arrival_date_day_of_month']]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>arrival_date_year</th>
      <th>arrival_date_month_index</th>
      <th>arrival_date_day_of_month</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2015</td>
      <td>7</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2015</td>
      <td>7</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2015</td>
      <td>7</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2015</td>
      <td>7</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2015</td>
      <td>7</td>
      <td>1</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>119385</th>
      <td>2017</td>
      <td>8</td>
      <td>30</td>
    </tr>
    <tr>
      <th>119386</th>
      <td>2017</td>
      <td>8</td>
      <td>31</td>
    </tr>
    <tr>
      <th>119387</th>
      <td>2017</td>
      <td>8</td>
      <td>31</td>
    </tr>
    <tr>
      <th>119388</th>
      <td>2017</td>
      <td>8</td>
      <td>31</td>
    </tr>
    <tr>
      <th>119389</th>
      <td>2017</td>
      <td>8</td>
      <td>29</td>
    </tr>
  </tbody>
</table>
<p>87230 rows × 3 columns</p>
</div>




```python
#using concatenation to join year + month + date for date format (convert them to string )
```


```python
df2['arrival_date'] = df2['arrival_date_year'].astype(str) + '-' + df2['arrival_date_month_index'].astype(str) + '-' + df2['arrival_date_day_of_month'].astype(str)
```


```python
df2.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>hotel</th>
      <th>is_canceled</th>
      <th>lead_time</th>
      <th>arrival_date_year</th>
      <th>arrival_date_month</th>
      <th>arrival_date_week_number</th>
      <th>arrival_date_day_of_month</th>
      <th>stays_in_weekend_nights</th>
      <th>stays_in_week_nights</th>
      <th>adults</th>
      <th>...</th>
      <th>company</th>
      <th>days_in_waiting_list</th>
      <th>customer_type</th>
      <th>adr</th>
      <th>required_car_parking_spaces</th>
      <th>total_of_special_requests</th>
      <th>reservation_status</th>
      <th>reservation_status_date</th>
      <th>arrival_date_month_index</th>
      <th>arrival_date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>342</td>
      <td>2015</td>
      <td>July</td>
      <td>27</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>...</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>0.0</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>7/1/2015</td>
      <td>7</td>
      <td>2015-7-1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>737</td>
      <td>2015</td>
      <td>July</td>
      <td>27</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>...</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>0.0</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>7/1/2015</td>
      <td>7</td>
      <td>2015-7-1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>7</td>
      <td>2015</td>
      <td>July</td>
      <td>27</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>...</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>75.0</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>7/2/2015</td>
      <td>7</td>
      <td>2015-7-1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>13</td>
      <td>2015</td>
      <td>July</td>
      <td>27</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>...</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>75.0</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>7/2/2015</td>
      <td>7</td>
      <td>2015-7-1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>14</td>
      <td>2015</td>
      <td>July</td>
      <td>27</td>
      <td>1</td>
      <td>0</td>
      <td>2</td>
      <td>2</td>
      <td>...</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>98.0</td>
      <td>0</td>
      <td>1</td>
      <td>Check-Out</td>
      <td>7/3/2015</td>
      <td>7</td>
      <td>2015-7-1</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 34 columns</p>
</div>




```python
# need table of sum of guests and grouping 'arrival_date' column
```


```python
guest_f = df2.groupby('arrival_date').size().reset_index(name='Sum of Rows')
```


```python
guest_f
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>arrival_date</th>
      <th>Sum of Rows</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2015-10-1</td>
      <td>93</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2015-10-10</td>
      <td>104</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2015-10-11</td>
      <td>75</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2015-10-12</td>
      <td>122</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2015-10-13</td>
      <td>69</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>788</th>
      <td>2017-8-5</td>
      <td>140</td>
    </tr>
    <tr>
      <th>789</th>
      <td>2017-8-6</td>
      <td>140</td>
    </tr>
    <tr>
      <th>790</th>
      <td>2017-8-7</td>
      <td>195</td>
    </tr>
    <tr>
      <th>791</th>
      <td>2017-8-8</td>
      <td>123</td>
    </tr>
    <tr>
      <th>792</th>
      <td>2017-8-9</td>
      <td>122</td>
    </tr>
  </tbody>
</table>
<p>793 rows × 2 columns</p>
</div>




```python
#convert 'arrival_date' to date_time format for analysis
```


```python
guest_f['arrival_date'] = pd.to_datetime(guest_f['arrival_date'])
```


```python
guest_f
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>arrival_date</th>
      <th>Sum of Rows</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2015-10-01</td>
      <td>93</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2015-10-10</td>
      <td>104</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2015-10-11</td>
      <td>75</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2015-10-12</td>
      <td>122</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2015-10-13</td>
      <td>69</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>788</th>
      <td>2017-08-05</td>
      <td>140</td>
    </tr>
    <tr>
      <th>789</th>
      <td>2017-08-06</td>
      <td>140</td>
    </tr>
    <tr>
      <th>790</th>
      <td>2017-08-07</td>
      <td>195</td>
    </tr>
    <tr>
      <th>791</th>
      <td>2017-08-08</td>
      <td>123</td>
    </tr>
    <tr>
      <th>792</th>
      <td>2017-08-09</td>
      <td>122</td>
    </tr>
  </tbody>
</table>
<p>793 rows × 2 columns</p>
</div>




```python
guest_f.columns = ['arrival_date','Sum of Guests']
```


```python
guest_f.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>arrival_date</th>
      <th>Sum of Guests</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2015-10-01</td>
      <td>93</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2015-10-10</td>
      <td>104</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2015-10-11</td>
      <td>75</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2015-10-12</td>
      <td>122</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2015-10-13</td>
      <td>69</td>
    </tr>
  </tbody>
</table>
</div>




```python
guest_f.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 793 entries, 0 to 792
    Data columns (total 2 columns):
     #   Column         Non-Null Count  Dtype         
    ---  ------         --------------  -----         
     0   arrival_date   793 non-null    datetime64[ns]
     1   Sum of Guests  793 non-null    int64         
    dtypes: datetime64[ns](1), int64(1)
    memory usage: 12.5 KB



```python
guest_f
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>arrival_date</th>
      <th>Sum of Guests</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2015-10-01</td>
      <td>93</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2015-10-10</td>
      <td>104</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2015-10-11</td>
      <td>75</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2015-10-12</td>
      <td>122</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2015-10-13</td>
      <td>69</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>788</th>
      <td>2017-08-05</td>
      <td>140</td>
    </tr>
    <tr>
      <th>789</th>
      <td>2017-08-06</td>
      <td>140</td>
    </tr>
    <tr>
      <th>790</th>
      <td>2017-08-07</td>
      <td>195</td>
    </tr>
    <tr>
      <th>791</th>
      <td>2017-08-08</td>
      <td>123</td>
    </tr>
    <tr>
      <th>792</th>
      <td>2017-08-09</td>
      <td>122</td>
    </tr>
  </tbody>
</table>
<p>793 rows × 2 columns</p>
</div>




```python
plt.figure(figsize=(16, 8))
plt.bar(guest_f['arrival_date'], guest_f['Sum of Guests'])
plt.title('Sum of Guests Over Time')
plt.xlabel('Arrival Date')
plt.ylabel('Sum of Guests')
plt.xticks(rotation=90)
plt.tight_layout()
plt.show()
```


    
![png](output_75_0.png)
    



```python
plt.figure(figsize=(16, 8))
plt.bar(guest_f['arrival_date'], guest_f['Sum of Guests'])
plt.axhline(y=guest_f['Sum of Guests'].mean(), color='red', linestyle='--', label='Mean')
plt.title('Sum of Guests Over Time with Mean Line')
plt.xlabel('Arrival Date')
plt.ylabel('Sum of Guests')
plt.xticks(rotation=90)
plt.legend()  # Add a legend to the plot
plt.tight_layout()
plt.show()
```


    
![png](output_76_0.png)
    



```python
#The red line shows the aveage no. of guests
```
