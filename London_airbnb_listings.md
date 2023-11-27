```python
import pandas as pd
import numpy as np
```


```python
df = pd.read_csv(r"/Users/gurudarshan/UOG/Projects/untitled folder/listings.csv")
```

    /var/folders/sy/gwh3by9524761shnjb3l2fnh0000gp/T/ipykernel_18812/210488926.py:1: DtypeWarning: Columns (17) have mixed types. Specify dtype option on import or set low_memory=False.
      df = pd.read_csv(r"/Users/gurudarshan/UOG/Projects/untitled folder/listings.csv")



```python
df = pd.read_csv("/Users/gurudarshan/UOG/Projects/untitled folder/listings.csv", low_memory=False)

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
      <th>id</th>
      <th>name</th>
      <th>host_id</th>
      <th>host_name</th>
      <th>neighbourhood_group</th>
      <th>neighbourhood</th>
      <th>latitude</th>
      <th>longitude</th>
      <th>room_type</th>
      <th>price</th>
      <th>minimum_nights</th>
      <th>number_of_reviews</th>
      <th>last_review</th>
      <th>reviews_per_month</th>
      <th>calculated_host_listings_count</th>
      <th>availability_365</th>
      <th>number_of_reviews_ltm</th>
      <th>license</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>13913</td>
      <td>Rental unit in Islington · ★4.80 · 1 bedroom ·...</td>
      <td>54730</td>
      <td>Alina</td>
      <td>NaN</td>
      <td>Islington</td>
      <td>51.56861</td>
      <td>-0.11270</td>
      <td>Private room</td>
      <td>79</td>
      <td>1</td>
      <td>41</td>
      <td>2022-12-11</td>
      <td>0.26</td>
      <td>2</td>
      <td>360</td>
      <td>11</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15400</td>
      <td>Rental unit in London · ★4.80 · 1 bedroom · 1 ...</td>
      <td>60302</td>
      <td>Philippa</td>
      <td>NaN</td>
      <td>Kensington and Chelsea</td>
      <td>51.48780</td>
      <td>-0.16813</td>
      <td>Entire home/apt</td>
      <td>150</td>
      <td>7</td>
      <td>94</td>
      <td>2023-05-01</td>
      <td>0.56</td>
      <td>1</td>
      <td>73</td>
      <td>5</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>92644</td>
      <td>Rental unit in Earlsfield · ★4.57 · 1 bedroom ...</td>
      <td>498201</td>
      <td>Dee Dee</td>
      <td>NaN</td>
      <td>Wandsworth</td>
      <td>51.44201</td>
      <td>-0.18739</td>
      <td>Private room</td>
      <td>42</td>
      <td>2</td>
      <td>216</td>
      <td>2022-10-29</td>
      <td>1.45</td>
      <td>1</td>
      <td>217</td>
      <td>9</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>17402</td>
      <td>Rental unit in London · ★4.76 · 3 bedrooms · 3...</td>
      <td>67564</td>
      <td>Liz</td>
      <td>NaN</td>
      <td>Westminster</td>
      <td>51.52195</td>
      <td>-0.14094</td>
      <td>Entire home/apt</td>
      <td>476</td>
      <td>3</td>
      <td>54</td>
      <td>2022-11-19</td>
      <td>0.36</td>
      <td>9</td>
      <td>300</td>
      <td>4</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>93015</td>
      <td>Rental unit in Hammersmith · ★4.82 · 2 bedroom...</td>
      <td>499704</td>
      <td>Sarah</td>
      <td>NaN</td>
      <td>Hammersmith and Fulham</td>
      <td>51.49993</td>
      <td>-0.21707</td>
      <td>Entire home/apt</td>
      <td>175</td>
      <td>5</td>
      <td>38</td>
      <td>2022-09-30</td>
      <td>0.27</td>
      <td>1</td>
      <td>40</td>
      <td>2</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Variety of data under one column
#Split column 'name' into multiple columns so we can extract more data for analysis
```


```python
df['name']
```




    0        Rental unit in Islington · ★4.80 · 1 bedroom ·...
    1        Rental unit in London · ★4.80 · 1 bedroom · 1 ...
    2        Rental unit in Earlsfield · ★4.57 · 1 bedroom ...
    3        Rental unit in London · ★4.76 · 3 bedrooms · 3...
    4        Rental unit in Hammersmith · ★4.82 · 2 bedroom...
                                   ...                        
    87942    Rental unit in Greater London · ★New · 1 bedro...
    87943    Rental unit in Greater London · ★New · 1 bedro...
    87944    Home in Greater London · ★New · 1 bedroom · 5 ...
    87945    Home in Greater London · ★New · 5 bedrooms · 5...
    87946    Rental unit in Greater London · ★New · 2 bedro...
    Name: name, Length: 87947, dtype: object




```python
df[['Property_Name', 'Property_Rating', 'Bedrooms', 'Beds', 'Bathrooms']] = df['name'].str.split('·', expand=True)
```


```python
#New columns have been added to the end of the table.

#('Property_Name','Property_Rating', 'Bedrooms', 'Beds', 'Bathrooms')
```


```python
df.columns
```




    Index(['id', 'name', 'host_id', 'host_name', 'neighbourhood_group',
           'neighbourhood', 'latitude', 'longitude', 'room_type', 'price',
           'minimum_nights', 'number_of_reviews', 'last_review',
           'reviews_per_month', 'calculated_host_listings_count',
           'availability_365', 'number_of_reviews_ltm', 'license', 'Property_Name',
           'Property_Rating', 'Bedrooms', 'Beds', 'Bathrooms'],
          dtype='object')




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
      <th>id</th>
      <th>name</th>
      <th>host_id</th>
      <th>host_name</th>
      <th>neighbourhood_group</th>
      <th>neighbourhood</th>
      <th>latitude</th>
      <th>longitude</th>
      <th>room_type</th>
      <th>price</th>
      <th>...</th>
      <th>reviews_per_month</th>
      <th>calculated_host_listings_count</th>
      <th>availability_365</th>
      <th>number_of_reviews_ltm</th>
      <th>license</th>
      <th>Property_Name</th>
      <th>Property_Rating</th>
      <th>Bedrooms</th>
      <th>Beds</th>
      <th>Bathrooms</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>13913</td>
      <td>Rental unit in Islington · ★4.80 · 1 bedroom ·...</td>
      <td>54730</td>
      <td>Alina</td>
      <td>NaN</td>
      <td>Islington</td>
      <td>51.56861</td>
      <td>-0.11270</td>
      <td>Private room</td>
      <td>79</td>
      <td>...</td>
      <td>0.26</td>
      <td>2</td>
      <td>360</td>
      <td>11</td>
      <td>NaN</td>
      <td>Rental unit in Islington</td>
      <td>★4.80</td>
      <td>1 bedroom</td>
      <td>1 bed</td>
      <td>1 shared bath</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15400</td>
      <td>Rental unit in London · ★4.80 · 1 bedroom · 1 ...</td>
      <td>60302</td>
      <td>Philippa</td>
      <td>NaN</td>
      <td>Kensington and Chelsea</td>
      <td>51.48780</td>
      <td>-0.16813</td>
      <td>Entire home/apt</td>
      <td>150</td>
      <td>...</td>
      <td>0.56</td>
      <td>1</td>
      <td>73</td>
      <td>5</td>
      <td>NaN</td>
      <td>Rental unit in London</td>
      <td>★4.80</td>
      <td>1 bedroom</td>
      <td>1 bed</td>
      <td>1 bath</td>
    </tr>
    <tr>
      <th>2</th>
      <td>92644</td>
      <td>Rental unit in Earlsfield · ★4.57 · 1 bedroom ...</td>
      <td>498201</td>
      <td>Dee Dee</td>
      <td>NaN</td>
      <td>Wandsworth</td>
      <td>51.44201</td>
      <td>-0.18739</td>
      <td>Private room</td>
      <td>42</td>
      <td>...</td>
      <td>1.45</td>
      <td>1</td>
      <td>217</td>
      <td>9</td>
      <td>NaN</td>
      <td>Rental unit in Earlsfield</td>
      <td>★4.57</td>
      <td>1 bedroom</td>
      <td>2 beds</td>
      <td>1.5 shared baths</td>
    </tr>
    <tr>
      <th>3</th>
      <td>17402</td>
      <td>Rental unit in London · ★4.76 · 3 bedrooms · 3...</td>
      <td>67564</td>
      <td>Liz</td>
      <td>NaN</td>
      <td>Westminster</td>
      <td>51.52195</td>
      <td>-0.14094</td>
      <td>Entire home/apt</td>
      <td>476</td>
      <td>...</td>
      <td>0.36</td>
      <td>9</td>
      <td>300</td>
      <td>4</td>
      <td>NaN</td>
      <td>Rental unit in London</td>
      <td>★4.76</td>
      <td>3 bedrooms</td>
      <td>3 beds</td>
      <td>2 baths</td>
    </tr>
    <tr>
      <th>4</th>
      <td>93015</td>
      <td>Rental unit in Hammersmith · ★4.82 · 2 bedroom...</td>
      <td>499704</td>
      <td>Sarah</td>
      <td>NaN</td>
      <td>Hammersmith and Fulham</td>
      <td>51.49993</td>
      <td>-0.21707</td>
      <td>Entire home/apt</td>
      <td>175</td>
      <td>...</td>
      <td>0.27</td>
      <td>1</td>
      <td>40</td>
      <td>2</td>
      <td>NaN</td>
      <td>Rental unit in Hammersmith</td>
      <td>★4.82</td>
      <td>2 bedrooms</td>
      <td>3 beds</td>
      <td>1 bath</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 23 columns</p>
</div>




```python
#Need to get rid of unrequired characters (start symbol in 'Property_Rating' column) 
```


```python
df['New_Property_Rating'] = df['Property_Rating'].str.slice(-4)

```


```python
#We lose data as it appears that there white space end of string.
```


```python
#Now removing all characters except last 5 chartacter of string to keep required data.
```


```python
df['Property_Rating'] = df['Property_Rating'].str.slice(-5)

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
      <th>id</th>
      <th>name</th>
      <th>host_id</th>
      <th>host_name</th>
      <th>neighbourhood_group</th>
      <th>neighbourhood</th>
      <th>latitude</th>
      <th>longitude</th>
      <th>room_type</th>
      <th>price</th>
      <th>...</th>
      <th>calculated_host_listings_count</th>
      <th>availability_365</th>
      <th>number_of_reviews_ltm</th>
      <th>license</th>
      <th>Property_Name</th>
      <th>Property_Rating</th>
      <th>Bedrooms</th>
      <th>Beds</th>
      <th>Bathrooms</th>
      <th>New_Property_Rating</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>13913</td>
      <td>Rental unit in Islington · ★4.80 · 1 bedroom ·...</td>
      <td>54730</td>
      <td>Alina</td>
      <td>NaN</td>
      <td>Islington</td>
      <td>51.56861</td>
      <td>-0.11270</td>
      <td>Private room</td>
      <td>79</td>
      <td>...</td>
      <td>2</td>
      <td>360</td>
      <td>11</td>
      <td>NaN</td>
      <td>Rental unit in Islington</td>
      <td>4.80</td>
      <td>1 bedroom</td>
      <td>1 bed</td>
      <td>1 shared bath</td>
      <td>.80</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15400</td>
      <td>Rental unit in London · ★4.80 · 1 bedroom · 1 ...</td>
      <td>60302</td>
      <td>Philippa</td>
      <td>NaN</td>
      <td>Kensington and Chelsea</td>
      <td>51.48780</td>
      <td>-0.16813</td>
      <td>Entire home/apt</td>
      <td>150</td>
      <td>...</td>
      <td>1</td>
      <td>73</td>
      <td>5</td>
      <td>NaN</td>
      <td>Rental unit in London</td>
      <td>4.80</td>
      <td>1 bedroom</td>
      <td>1 bed</td>
      <td>1 bath</td>
      <td>.80</td>
    </tr>
    <tr>
      <th>2</th>
      <td>92644</td>
      <td>Rental unit in Earlsfield · ★4.57 · 1 bedroom ...</td>
      <td>498201</td>
      <td>Dee Dee</td>
      <td>NaN</td>
      <td>Wandsworth</td>
      <td>51.44201</td>
      <td>-0.18739</td>
      <td>Private room</td>
      <td>42</td>
      <td>...</td>
      <td>1</td>
      <td>217</td>
      <td>9</td>
      <td>NaN</td>
      <td>Rental unit in Earlsfield</td>
      <td>4.57</td>
      <td>1 bedroom</td>
      <td>2 beds</td>
      <td>1.5 shared baths</td>
      <td>.57</td>
    </tr>
    <tr>
      <th>3</th>
      <td>17402</td>
      <td>Rental unit in London · ★4.76 · 3 bedrooms · 3...</td>
      <td>67564</td>
      <td>Liz</td>
      <td>NaN</td>
      <td>Westminster</td>
      <td>51.52195</td>
      <td>-0.14094</td>
      <td>Entire home/apt</td>
      <td>476</td>
      <td>...</td>
      <td>9</td>
      <td>300</td>
      <td>4</td>
      <td>NaN</td>
      <td>Rental unit in London</td>
      <td>4.76</td>
      <td>3 bedrooms</td>
      <td>3 beds</td>
      <td>2 baths</td>
      <td>.76</td>
    </tr>
    <tr>
      <th>4</th>
      <td>93015</td>
      <td>Rental unit in Hammersmith · ★4.82 · 2 bedroom...</td>
      <td>499704</td>
      <td>Sarah</td>
      <td>NaN</td>
      <td>Hammersmith and Fulham</td>
      <td>51.49993</td>
      <td>-0.21707</td>
      <td>Entire home/apt</td>
      <td>175</td>
      <td>...</td>
      <td>1</td>
      <td>40</td>
      <td>2</td>
      <td>NaN</td>
      <td>Rental unit in Hammersmith</td>
      <td>4.82</td>
      <td>2 bedrooms</td>
      <td>3 beds</td>
      <td>1 bath</td>
      <td>.82</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 24 columns</p>
</div>




```python
#Column to show length of string to notice whitespace in string to remove
```


```python
df['Property_Rating_Length'] = df['Property_Rating'].str.len()

```


```python
df
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
      <th>id</th>
      <th>name</th>
      <th>host_id</th>
      <th>host_name</th>
      <th>neighbourhood_group</th>
      <th>neighbourhood</th>
      <th>latitude</th>
      <th>longitude</th>
      <th>room_type</th>
      <th>price</th>
      <th>...</th>
      <th>availability_365</th>
      <th>number_of_reviews_ltm</th>
      <th>license</th>
      <th>Property_Name</th>
      <th>Property_Rating</th>
      <th>Bedrooms</th>
      <th>Beds</th>
      <th>Bathrooms</th>
      <th>New_Property_Rating</th>
      <th>Property_Rating_Length</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>13913</td>
      <td>Rental unit in Islington · ★4.80 · 1 bedroom ·...</td>
      <td>54730</td>
      <td>Alina</td>
      <td>NaN</td>
      <td>Islington</td>
      <td>51.568610</td>
      <td>-0.112700</td>
      <td>Private room</td>
      <td>79</td>
      <td>...</td>
      <td>360</td>
      <td>11</td>
      <td>NaN</td>
      <td>Rental unit in Islington</td>
      <td>4.80</td>
      <td>1 bedroom</td>
      <td>1 bed</td>
      <td>1 shared bath</td>
      <td>.80</td>
      <td>5</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15400</td>
      <td>Rental unit in London · ★4.80 · 1 bedroom · 1 ...</td>
      <td>60302</td>
      <td>Philippa</td>
      <td>NaN</td>
      <td>Kensington and Chelsea</td>
      <td>51.487800</td>
      <td>-0.168130</td>
      <td>Entire home/apt</td>
      <td>150</td>
      <td>...</td>
      <td>73</td>
      <td>5</td>
      <td>NaN</td>
      <td>Rental unit in London</td>
      <td>4.80</td>
      <td>1 bedroom</td>
      <td>1 bed</td>
      <td>1 bath</td>
      <td>.80</td>
      <td>5</td>
    </tr>
    <tr>
      <th>2</th>
      <td>92644</td>
      <td>Rental unit in Earlsfield · ★4.57 · 1 bedroom ...</td>
      <td>498201</td>
      <td>Dee Dee</td>
      <td>NaN</td>
      <td>Wandsworth</td>
      <td>51.442010</td>
      <td>-0.187390</td>
      <td>Private room</td>
      <td>42</td>
      <td>...</td>
      <td>217</td>
      <td>9</td>
      <td>NaN</td>
      <td>Rental unit in Earlsfield</td>
      <td>4.57</td>
      <td>1 bedroom</td>
      <td>2 beds</td>
      <td>1.5 shared baths</td>
      <td>.57</td>
      <td>5</td>
    </tr>
    <tr>
      <th>3</th>
      <td>17402</td>
      <td>Rental unit in London · ★4.76 · 3 bedrooms · 3...</td>
      <td>67564</td>
      <td>Liz</td>
      <td>NaN</td>
      <td>Westminster</td>
      <td>51.521950</td>
      <td>-0.140940</td>
      <td>Entire home/apt</td>
      <td>476</td>
      <td>...</td>
      <td>300</td>
      <td>4</td>
      <td>NaN</td>
      <td>Rental unit in London</td>
      <td>4.76</td>
      <td>3 bedrooms</td>
      <td>3 beds</td>
      <td>2 baths</td>
      <td>.76</td>
      <td>5</td>
    </tr>
    <tr>
      <th>4</th>
      <td>93015</td>
      <td>Rental unit in Hammersmith · ★4.82 · 2 bedroom...</td>
      <td>499704</td>
      <td>Sarah</td>
      <td>NaN</td>
      <td>Hammersmith and Fulham</td>
      <td>51.499930</td>
      <td>-0.217070</td>
      <td>Entire home/apt</td>
      <td>175</td>
      <td>...</td>
      <td>40</td>
      <td>2</td>
      <td>NaN</td>
      <td>Rental unit in Hammersmith</td>
      <td>4.82</td>
      <td>2 bedrooms</td>
      <td>3 beds</td>
      <td>1 bath</td>
      <td>.82</td>
      <td>5</td>
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
      <th>87942</th>
      <td>973781286754517228</td>
      <td>Rental unit in Greater London · ★New · 1 bedro...</td>
      <td>498408783</td>
      <td>Sal</td>
      <td>NaN</td>
      <td>Westminster</td>
      <td>51.514860</td>
      <td>-0.135980</td>
      <td>Entire home/apt</td>
      <td>275</td>
      <td>...</td>
      <td>239</td>
      <td>0</td>
      <td>NaN</td>
      <td>Rental unit in Greater London</td>
      <td>★New</td>
      <td>1 bedroom</td>
      <td>2 beds</td>
      <td>1 bath</td>
      <td>New</td>
      <td>5</td>
    </tr>
    <tr>
      <th>87943</th>
      <td>973801695874775338</td>
      <td>Rental unit in Greater London · ★New · 1 bedro...</td>
      <td>36645347</td>
      <td>Josie</td>
      <td>NaN</td>
      <td>Southwark</td>
      <td>51.459042</td>
      <td>-0.055458</td>
      <td>Entire home/apt</td>
      <td>145</td>
      <td>...</td>
      <td>88</td>
      <td>0</td>
      <td>NaN</td>
      <td>Rental unit in Greater London</td>
      <td>★New</td>
      <td>1 bedroom</td>
      <td>1 bed</td>
      <td>1 bath</td>
      <td>New</td>
      <td>5</td>
    </tr>
    <tr>
      <th>87944</th>
      <td>973811685656289740</td>
      <td>Home in Greater London · ★New · 1 bedroom · 5 ...</td>
      <td>340514057</td>
      <td>Mal</td>
      <td>NaN</td>
      <td>Merton</td>
      <td>51.406100</td>
      <td>-0.236126</td>
      <td>Private room</td>
      <td>160</td>
      <td>...</td>
      <td>80</td>
      <td>0</td>
      <td>NaN</td>
      <td>Home in Greater London</td>
      <td>★New</td>
      <td>1 bedroom</td>
      <td>5 beds</td>
      <td>2 shared baths</td>
      <td>New</td>
      <td>5</td>
    </tr>
    <tr>
      <th>87945</th>
      <td>973882998775927897</td>
      <td>Home in Greater London · ★New · 5 bedrooms · 5...</td>
      <td>439074505</td>
      <td>Travelnest</td>
      <td>NaN</td>
      <td>Hounslow</td>
      <td>51.450997</td>
      <td>-0.444319</td>
      <td>Entire home/apt</td>
      <td>680</td>
      <td>...</td>
      <td>364</td>
      <td>0</td>
      <td>NaN</td>
      <td>Home in Greater London</td>
      <td>★New</td>
      <td>5 bedrooms</td>
      <td>5 beds</td>
      <td>1 bath</td>
      <td>New</td>
      <td>5</td>
    </tr>
    <tr>
      <th>87946</th>
      <td>973895808066047620</td>
      <td>Rental unit in Greater London · ★New · 2 bedro...</td>
      <td>475112423</td>
      <td>Lea</td>
      <td>NaN</td>
      <td>City of London</td>
      <td>51.515970</td>
      <td>-0.111342</td>
      <td>Entire home/apt</td>
      <td>170</td>
      <td>...</td>
      <td>297</td>
      <td>0</td>
      <td>NaN</td>
      <td>Rental unit in Greater London</td>
      <td>★New</td>
      <td>2 bedrooms</td>
      <td>3 beds</td>
      <td>1 bath</td>
      <td>New</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
<p>87947 rows × 25 columns</p>
</div>




```python
#Removing last character (whitespace)
```


```python
df['Property_Rating'] = df['Property_Rating'].str.slice(0, -1)

```


```python
df
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
      <th>id</th>
      <th>name</th>
      <th>host_id</th>
      <th>host_name</th>
      <th>neighbourhood_group</th>
      <th>neighbourhood</th>
      <th>latitude</th>
      <th>longitude</th>
      <th>room_type</th>
      <th>price</th>
      <th>...</th>
      <th>availability_365</th>
      <th>number_of_reviews_ltm</th>
      <th>license</th>
      <th>Property_Name</th>
      <th>Property_Rating</th>
      <th>Bedrooms</th>
      <th>Beds</th>
      <th>Bathrooms</th>
      <th>New_Property_Rating</th>
      <th>Property_Rating_Length</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>13913</td>
      <td>Rental unit in Islington · ★4.80 · 1 bedroom ·...</td>
      <td>54730</td>
      <td>Alina</td>
      <td>NaN</td>
      <td>Islington</td>
      <td>51.568610</td>
      <td>-0.112700</td>
      <td>Private room</td>
      <td>79</td>
      <td>...</td>
      <td>360</td>
      <td>11</td>
      <td>NaN</td>
      <td>Rental unit in Islington</td>
      <td>4.80</td>
      <td>1 bedroom</td>
      <td>1 bed</td>
      <td>1 shared bath</td>
      <td>.80</td>
      <td>5</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15400</td>
      <td>Rental unit in London · ★4.80 · 1 bedroom · 1 ...</td>
      <td>60302</td>
      <td>Philippa</td>
      <td>NaN</td>
      <td>Kensington and Chelsea</td>
      <td>51.487800</td>
      <td>-0.168130</td>
      <td>Entire home/apt</td>
      <td>150</td>
      <td>...</td>
      <td>73</td>
      <td>5</td>
      <td>NaN</td>
      <td>Rental unit in London</td>
      <td>4.80</td>
      <td>1 bedroom</td>
      <td>1 bed</td>
      <td>1 bath</td>
      <td>.80</td>
      <td>5</td>
    </tr>
    <tr>
      <th>2</th>
      <td>92644</td>
      <td>Rental unit in Earlsfield · ★4.57 · 1 bedroom ...</td>
      <td>498201</td>
      <td>Dee Dee</td>
      <td>NaN</td>
      <td>Wandsworth</td>
      <td>51.442010</td>
      <td>-0.187390</td>
      <td>Private room</td>
      <td>42</td>
      <td>...</td>
      <td>217</td>
      <td>9</td>
      <td>NaN</td>
      <td>Rental unit in Earlsfield</td>
      <td>4.57</td>
      <td>1 bedroom</td>
      <td>2 beds</td>
      <td>1.5 shared baths</td>
      <td>.57</td>
      <td>5</td>
    </tr>
    <tr>
      <th>3</th>
      <td>17402</td>
      <td>Rental unit in London · ★4.76 · 3 bedrooms · 3...</td>
      <td>67564</td>
      <td>Liz</td>
      <td>NaN</td>
      <td>Westminster</td>
      <td>51.521950</td>
      <td>-0.140940</td>
      <td>Entire home/apt</td>
      <td>476</td>
      <td>...</td>
      <td>300</td>
      <td>4</td>
      <td>NaN</td>
      <td>Rental unit in London</td>
      <td>4.76</td>
      <td>3 bedrooms</td>
      <td>3 beds</td>
      <td>2 baths</td>
      <td>.76</td>
      <td>5</td>
    </tr>
    <tr>
      <th>4</th>
      <td>93015</td>
      <td>Rental unit in Hammersmith · ★4.82 · 2 bedroom...</td>
      <td>499704</td>
      <td>Sarah</td>
      <td>NaN</td>
      <td>Hammersmith and Fulham</td>
      <td>51.499930</td>
      <td>-0.217070</td>
      <td>Entire home/apt</td>
      <td>175</td>
      <td>...</td>
      <td>40</td>
      <td>2</td>
      <td>NaN</td>
      <td>Rental unit in Hammersmith</td>
      <td>4.82</td>
      <td>2 bedrooms</td>
      <td>3 beds</td>
      <td>1 bath</td>
      <td>.82</td>
      <td>5</td>
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
      <th>87942</th>
      <td>973781286754517228</td>
      <td>Rental unit in Greater London · ★New · 1 bedro...</td>
      <td>498408783</td>
      <td>Sal</td>
      <td>NaN</td>
      <td>Westminster</td>
      <td>51.514860</td>
      <td>-0.135980</td>
      <td>Entire home/apt</td>
      <td>275</td>
      <td>...</td>
      <td>239</td>
      <td>0</td>
      <td>NaN</td>
      <td>Rental unit in Greater London</td>
      <td>★New</td>
      <td>1 bedroom</td>
      <td>2 beds</td>
      <td>1 bath</td>
      <td>New</td>
      <td>5</td>
    </tr>
    <tr>
      <th>87943</th>
      <td>973801695874775338</td>
      <td>Rental unit in Greater London · ★New · 1 bedro...</td>
      <td>36645347</td>
      <td>Josie</td>
      <td>NaN</td>
      <td>Southwark</td>
      <td>51.459042</td>
      <td>-0.055458</td>
      <td>Entire home/apt</td>
      <td>145</td>
      <td>...</td>
      <td>88</td>
      <td>0</td>
      <td>NaN</td>
      <td>Rental unit in Greater London</td>
      <td>★New</td>
      <td>1 bedroom</td>
      <td>1 bed</td>
      <td>1 bath</td>
      <td>New</td>
      <td>5</td>
    </tr>
    <tr>
      <th>87944</th>
      <td>973811685656289740</td>
      <td>Home in Greater London · ★New · 1 bedroom · 5 ...</td>
      <td>340514057</td>
      <td>Mal</td>
      <td>NaN</td>
      <td>Merton</td>
      <td>51.406100</td>
      <td>-0.236126</td>
      <td>Private room</td>
      <td>160</td>
      <td>...</td>
      <td>80</td>
      <td>0</td>
      <td>NaN</td>
      <td>Home in Greater London</td>
      <td>★New</td>
      <td>1 bedroom</td>
      <td>5 beds</td>
      <td>2 shared baths</td>
      <td>New</td>
      <td>5</td>
    </tr>
    <tr>
      <th>87945</th>
      <td>973882998775927897</td>
      <td>Home in Greater London · ★New · 5 bedrooms · 5...</td>
      <td>439074505</td>
      <td>Travelnest</td>
      <td>NaN</td>
      <td>Hounslow</td>
      <td>51.450997</td>
      <td>-0.444319</td>
      <td>Entire home/apt</td>
      <td>680</td>
      <td>...</td>
      <td>364</td>
      <td>0</td>
      <td>NaN</td>
      <td>Home in Greater London</td>
      <td>★New</td>
      <td>5 bedrooms</td>
      <td>5 beds</td>
      <td>1 bath</td>
      <td>New</td>
      <td>5</td>
    </tr>
    <tr>
      <th>87946</th>
      <td>973895808066047620</td>
      <td>Rental unit in Greater London · ★New · 2 bedro...</td>
      <td>475112423</td>
      <td>Lea</td>
      <td>NaN</td>
      <td>City of London</td>
      <td>51.515970</td>
      <td>-0.111342</td>
      <td>Entire home/apt</td>
      <td>170</td>
      <td>...</td>
      <td>297</td>
      <td>0</td>
      <td>NaN</td>
      <td>Rental unit in Greater London</td>
      <td>★New</td>
      <td>2 bedrooms</td>
      <td>3 beds</td>
      <td>1 bath</td>
      <td>New</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
<p>87947 rows × 25 columns</p>
</div>




```python
#Removing star symbol from "Property_Rating" column for new property rows
```


```python
df['Property_Rating'] = df['Property_Rating'].str.replace(r'[^0-9a-zA-Z.]', '', regex=True)
```


```python
df
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
      <th>id</th>
      <th>name</th>
      <th>host_id</th>
      <th>host_name</th>
      <th>neighbourhood_group</th>
      <th>neighbourhood</th>
      <th>latitude</th>
      <th>longitude</th>
      <th>room_type</th>
      <th>price</th>
      <th>...</th>
      <th>availability_365</th>
      <th>number_of_reviews_ltm</th>
      <th>license</th>
      <th>Property_Name</th>
      <th>Property_Rating</th>
      <th>Bedrooms</th>
      <th>Beds</th>
      <th>Bathrooms</th>
      <th>New_Property_Rating</th>
      <th>Property_Rating_Length</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>13913</td>
      <td>Rental unit in Islington · ★4.80 · 1 bedroom ·...</td>
      <td>54730</td>
      <td>Alina</td>
      <td>NaN</td>
      <td>Islington</td>
      <td>51.568610</td>
      <td>-0.112700</td>
      <td>Private room</td>
      <td>79</td>
      <td>...</td>
      <td>360</td>
      <td>11</td>
      <td>NaN</td>
      <td>Rental unit in Islington</td>
      <td>4.80</td>
      <td>1 bedroom</td>
      <td>1 bed</td>
      <td>1 shared bath</td>
      <td>.80</td>
      <td>5</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15400</td>
      <td>Rental unit in London · ★4.80 · 1 bedroom · 1 ...</td>
      <td>60302</td>
      <td>Philippa</td>
      <td>NaN</td>
      <td>Kensington and Chelsea</td>
      <td>51.487800</td>
      <td>-0.168130</td>
      <td>Entire home/apt</td>
      <td>150</td>
      <td>...</td>
      <td>73</td>
      <td>5</td>
      <td>NaN</td>
      <td>Rental unit in London</td>
      <td>4.80</td>
      <td>1 bedroom</td>
      <td>1 bed</td>
      <td>1 bath</td>
      <td>.80</td>
      <td>5</td>
    </tr>
    <tr>
      <th>2</th>
      <td>92644</td>
      <td>Rental unit in Earlsfield · ★4.57 · 1 bedroom ...</td>
      <td>498201</td>
      <td>Dee Dee</td>
      <td>NaN</td>
      <td>Wandsworth</td>
      <td>51.442010</td>
      <td>-0.187390</td>
      <td>Private room</td>
      <td>42</td>
      <td>...</td>
      <td>217</td>
      <td>9</td>
      <td>NaN</td>
      <td>Rental unit in Earlsfield</td>
      <td>4.57</td>
      <td>1 bedroom</td>
      <td>2 beds</td>
      <td>1.5 shared baths</td>
      <td>.57</td>
      <td>5</td>
    </tr>
    <tr>
      <th>3</th>
      <td>17402</td>
      <td>Rental unit in London · ★4.76 · 3 bedrooms · 3...</td>
      <td>67564</td>
      <td>Liz</td>
      <td>NaN</td>
      <td>Westminster</td>
      <td>51.521950</td>
      <td>-0.140940</td>
      <td>Entire home/apt</td>
      <td>476</td>
      <td>...</td>
      <td>300</td>
      <td>4</td>
      <td>NaN</td>
      <td>Rental unit in London</td>
      <td>4.76</td>
      <td>3 bedrooms</td>
      <td>3 beds</td>
      <td>2 baths</td>
      <td>.76</td>
      <td>5</td>
    </tr>
    <tr>
      <th>4</th>
      <td>93015</td>
      <td>Rental unit in Hammersmith · ★4.82 · 2 bedroom...</td>
      <td>499704</td>
      <td>Sarah</td>
      <td>NaN</td>
      <td>Hammersmith and Fulham</td>
      <td>51.499930</td>
      <td>-0.217070</td>
      <td>Entire home/apt</td>
      <td>175</td>
      <td>...</td>
      <td>40</td>
      <td>2</td>
      <td>NaN</td>
      <td>Rental unit in Hammersmith</td>
      <td>4.82</td>
      <td>2 bedrooms</td>
      <td>3 beds</td>
      <td>1 bath</td>
      <td>.82</td>
      <td>5</td>
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
      <th>87942</th>
      <td>973781286754517228</td>
      <td>Rental unit in Greater London · ★New · 1 bedro...</td>
      <td>498408783</td>
      <td>Sal</td>
      <td>NaN</td>
      <td>Westminster</td>
      <td>51.514860</td>
      <td>-0.135980</td>
      <td>Entire home/apt</td>
      <td>275</td>
      <td>...</td>
      <td>239</td>
      <td>0</td>
      <td>NaN</td>
      <td>Rental unit in Greater London</td>
      <td>New</td>
      <td>1 bedroom</td>
      <td>2 beds</td>
      <td>1 bath</td>
      <td>New</td>
      <td>5</td>
    </tr>
    <tr>
      <th>87943</th>
      <td>973801695874775338</td>
      <td>Rental unit in Greater London · ★New · 1 bedro...</td>
      <td>36645347</td>
      <td>Josie</td>
      <td>NaN</td>
      <td>Southwark</td>
      <td>51.459042</td>
      <td>-0.055458</td>
      <td>Entire home/apt</td>
      <td>145</td>
      <td>...</td>
      <td>88</td>
      <td>0</td>
      <td>NaN</td>
      <td>Rental unit in Greater London</td>
      <td>New</td>
      <td>1 bedroom</td>
      <td>1 bed</td>
      <td>1 bath</td>
      <td>New</td>
      <td>5</td>
    </tr>
    <tr>
      <th>87944</th>
      <td>973811685656289740</td>
      <td>Home in Greater London · ★New · 1 bedroom · 5 ...</td>
      <td>340514057</td>
      <td>Mal</td>
      <td>NaN</td>
      <td>Merton</td>
      <td>51.406100</td>
      <td>-0.236126</td>
      <td>Private room</td>
      <td>160</td>
      <td>...</td>
      <td>80</td>
      <td>0</td>
      <td>NaN</td>
      <td>Home in Greater London</td>
      <td>New</td>
      <td>1 bedroom</td>
      <td>5 beds</td>
      <td>2 shared baths</td>
      <td>New</td>
      <td>5</td>
    </tr>
    <tr>
      <th>87945</th>
      <td>973882998775927897</td>
      <td>Home in Greater London · ★New · 5 bedrooms · 5...</td>
      <td>439074505</td>
      <td>Travelnest</td>
      <td>NaN</td>
      <td>Hounslow</td>
      <td>51.450997</td>
      <td>-0.444319</td>
      <td>Entire home/apt</td>
      <td>680</td>
      <td>...</td>
      <td>364</td>
      <td>0</td>
      <td>NaN</td>
      <td>Home in Greater London</td>
      <td>New</td>
      <td>5 bedrooms</td>
      <td>5 beds</td>
      <td>1 bath</td>
      <td>New</td>
      <td>5</td>
    </tr>
    <tr>
      <th>87946</th>
      <td>973895808066047620</td>
      <td>Rental unit in Greater London · ★New · 2 bedro...</td>
      <td>475112423</td>
      <td>Lea</td>
      <td>NaN</td>
      <td>City of London</td>
      <td>51.515970</td>
      <td>-0.111342</td>
      <td>Entire home/apt</td>
      <td>170</td>
      <td>...</td>
      <td>297</td>
      <td>0</td>
      <td>NaN</td>
      <td>Rental unit in Greater London</td>
      <td>New</td>
      <td>2 bedrooms</td>
      <td>3 beds</td>
      <td>1 bath</td>
      <td>New</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
<p>87947 rows × 25 columns</p>
</div>




```python
#rechecking length of column (Now 4)
```


```python
df['Property_Rating_Length'] = df['Property_Rating'].str.len()

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
      <th>id</th>
      <th>name</th>
      <th>host_id</th>
      <th>host_name</th>
      <th>neighbourhood_group</th>
      <th>neighbourhood</th>
      <th>latitude</th>
      <th>longitude</th>
      <th>room_type</th>
      <th>price</th>
      <th>...</th>
      <th>availability_365</th>
      <th>number_of_reviews_ltm</th>
      <th>license</th>
      <th>Property_Name</th>
      <th>Property_Rating</th>
      <th>Bedrooms</th>
      <th>Beds</th>
      <th>Bathrooms</th>
      <th>New_Property_Rating</th>
      <th>Property_Rating_Length</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>13913</td>
      <td>Rental unit in Islington · ★4.80 · 1 bedroom ·...</td>
      <td>54730</td>
      <td>Alina</td>
      <td>NaN</td>
      <td>Islington</td>
      <td>51.56861</td>
      <td>-0.11270</td>
      <td>Private room</td>
      <td>79</td>
      <td>...</td>
      <td>360</td>
      <td>11</td>
      <td>NaN</td>
      <td>Rental unit in Islington</td>
      <td>4.80</td>
      <td>1 bedroom</td>
      <td>1 bed</td>
      <td>1 shared bath</td>
      <td>.80</td>
      <td>4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15400</td>
      <td>Rental unit in London · ★4.80 · 1 bedroom · 1 ...</td>
      <td>60302</td>
      <td>Philippa</td>
      <td>NaN</td>
      <td>Kensington and Chelsea</td>
      <td>51.48780</td>
      <td>-0.16813</td>
      <td>Entire home/apt</td>
      <td>150</td>
      <td>...</td>
      <td>73</td>
      <td>5</td>
      <td>NaN</td>
      <td>Rental unit in London</td>
      <td>4.80</td>
      <td>1 bedroom</td>
      <td>1 bed</td>
      <td>1 bath</td>
      <td>.80</td>
      <td>4</td>
    </tr>
    <tr>
      <th>2</th>
      <td>92644</td>
      <td>Rental unit in Earlsfield · ★4.57 · 1 bedroom ...</td>
      <td>498201</td>
      <td>Dee Dee</td>
      <td>NaN</td>
      <td>Wandsworth</td>
      <td>51.44201</td>
      <td>-0.18739</td>
      <td>Private room</td>
      <td>42</td>
      <td>...</td>
      <td>217</td>
      <td>9</td>
      <td>NaN</td>
      <td>Rental unit in Earlsfield</td>
      <td>4.57</td>
      <td>1 bedroom</td>
      <td>2 beds</td>
      <td>1.5 shared baths</td>
      <td>.57</td>
      <td>4</td>
    </tr>
    <tr>
      <th>3</th>
      <td>17402</td>
      <td>Rental unit in London · ★4.76 · 3 bedrooms · 3...</td>
      <td>67564</td>
      <td>Liz</td>
      <td>NaN</td>
      <td>Westminster</td>
      <td>51.52195</td>
      <td>-0.14094</td>
      <td>Entire home/apt</td>
      <td>476</td>
      <td>...</td>
      <td>300</td>
      <td>4</td>
      <td>NaN</td>
      <td>Rental unit in London</td>
      <td>4.76</td>
      <td>3 bedrooms</td>
      <td>3 beds</td>
      <td>2 baths</td>
      <td>.76</td>
      <td>4</td>
    </tr>
    <tr>
      <th>4</th>
      <td>93015</td>
      <td>Rental unit in Hammersmith · ★4.82 · 2 bedroom...</td>
      <td>499704</td>
      <td>Sarah</td>
      <td>NaN</td>
      <td>Hammersmith and Fulham</td>
      <td>51.49993</td>
      <td>-0.21707</td>
      <td>Entire home/apt</td>
      <td>175</td>
      <td>...</td>
      <td>40</td>
      <td>2</td>
      <td>NaN</td>
      <td>Rental unit in Hammersmith</td>
      <td>4.82</td>
      <td>2 bedrooms</td>
      <td>3 beds</td>
      <td>1 bath</td>
      <td>.82</td>
      <td>4</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 25 columns</p>
</div>




```python
#Need to remove 'bedroom' from Bedrooms column and convert to int data type 
```


```python
#lets check string length to determine if whitespace is present in string 
```


```python
df['Bedroom_Length'] = df['Bedrooms'].str.len()

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
      <th>id</th>
      <th>name</th>
      <th>host_id</th>
      <th>host_name</th>
      <th>neighbourhood_group</th>
      <th>neighbourhood</th>
      <th>latitude</th>
      <th>longitude</th>
      <th>room_type</th>
      <th>price</th>
      <th>...</th>
      <th>number_of_reviews_ltm</th>
      <th>license</th>
      <th>Property_Name</th>
      <th>Property_Rating</th>
      <th>Bedrooms</th>
      <th>Beds</th>
      <th>Bathrooms</th>
      <th>New_Property_Rating</th>
      <th>Property_Rating_Length</th>
      <th>Bedroom_Length</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>13913</td>
      <td>Rental unit in Islington · ★4.80 · 1 bedroom ·...</td>
      <td>54730</td>
      <td>Alina</td>
      <td>NaN</td>
      <td>Islington</td>
      <td>51.56861</td>
      <td>-0.11270</td>
      <td>Private room</td>
      <td>79</td>
      <td>...</td>
      <td>11</td>
      <td>NaN</td>
      <td>Rental unit in Islington</td>
      <td>4.80</td>
      <td>1 bedroom</td>
      <td>1 bed</td>
      <td>1 shared bath</td>
      <td>.80</td>
      <td>4</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15400</td>
      <td>Rental unit in London · ★4.80 · 1 bedroom · 1 ...</td>
      <td>60302</td>
      <td>Philippa</td>
      <td>NaN</td>
      <td>Kensington and Chelsea</td>
      <td>51.48780</td>
      <td>-0.16813</td>
      <td>Entire home/apt</td>
      <td>150</td>
      <td>...</td>
      <td>5</td>
      <td>NaN</td>
      <td>Rental unit in London</td>
      <td>4.80</td>
      <td>1 bedroom</td>
      <td>1 bed</td>
      <td>1 bath</td>
      <td>.80</td>
      <td>4</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>92644</td>
      <td>Rental unit in Earlsfield · ★4.57 · 1 bedroom ...</td>
      <td>498201</td>
      <td>Dee Dee</td>
      <td>NaN</td>
      <td>Wandsworth</td>
      <td>51.44201</td>
      <td>-0.18739</td>
      <td>Private room</td>
      <td>42</td>
      <td>...</td>
      <td>9</td>
      <td>NaN</td>
      <td>Rental unit in Earlsfield</td>
      <td>4.57</td>
      <td>1 bedroom</td>
      <td>2 beds</td>
      <td>1.5 shared baths</td>
      <td>.57</td>
      <td>4</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>17402</td>
      <td>Rental unit in London · ★4.76 · 3 bedrooms · 3...</td>
      <td>67564</td>
      <td>Liz</td>
      <td>NaN</td>
      <td>Westminster</td>
      <td>51.52195</td>
      <td>-0.14094</td>
      <td>Entire home/apt</td>
      <td>476</td>
      <td>...</td>
      <td>4</td>
      <td>NaN</td>
      <td>Rental unit in London</td>
      <td>4.76</td>
      <td>3 bedrooms</td>
      <td>3 beds</td>
      <td>2 baths</td>
      <td>.76</td>
      <td>4</td>
      <td>12.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>93015</td>
      <td>Rental unit in Hammersmith · ★4.82 · 2 bedroom...</td>
      <td>499704</td>
      <td>Sarah</td>
      <td>NaN</td>
      <td>Hammersmith and Fulham</td>
      <td>51.49993</td>
      <td>-0.21707</td>
      <td>Entire home/apt</td>
      <td>175</td>
      <td>...</td>
      <td>2</td>
      <td>NaN</td>
      <td>Rental unit in Hammersmith</td>
      <td>4.82</td>
      <td>2 bedrooms</td>
      <td>3 beds</td>
      <td>1 bath</td>
      <td>.82</td>
      <td>4</td>
      <td>12.0</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 26 columns</p>
</div>




```python
#11 characters in string and 9 can be calculated. possibly 1 whitespace in beginning and end of string.
```


```python
#Removing all characters except first 2 characters
```


```python
df['Bedrooms'] = df['Bedrooms'].str.slice(0, 2)
```


```python
#'bedroom' string has been removed from column 'Bedrooms'
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
      <th>id</th>
      <th>name</th>
      <th>host_id</th>
      <th>host_name</th>
      <th>neighbourhood_group</th>
      <th>neighbourhood</th>
      <th>latitude</th>
      <th>longitude</th>
      <th>room_type</th>
      <th>price</th>
      <th>...</th>
      <th>number_of_reviews_ltm</th>
      <th>license</th>
      <th>Property_Name</th>
      <th>Property_Rating</th>
      <th>Bedrooms</th>
      <th>Beds</th>
      <th>Bathrooms</th>
      <th>New_Property_Rating</th>
      <th>Property_Rating_Length</th>
      <th>Bedroom_Length</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>13913</td>
      <td>Rental unit in Islington · ★4.80 · 1 bedroom ·...</td>
      <td>54730</td>
      <td>Alina</td>
      <td>NaN</td>
      <td>Islington</td>
      <td>51.56861</td>
      <td>-0.11270</td>
      <td>Private room</td>
      <td>79</td>
      <td>...</td>
      <td>11</td>
      <td>NaN</td>
      <td>Rental unit in Islington</td>
      <td>4.80</td>
      <td>1</td>
      <td>1 bed</td>
      <td>1 shared bath</td>
      <td>.80</td>
      <td>4</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15400</td>
      <td>Rental unit in London · ★4.80 · 1 bedroom · 1 ...</td>
      <td>60302</td>
      <td>Philippa</td>
      <td>NaN</td>
      <td>Kensington and Chelsea</td>
      <td>51.48780</td>
      <td>-0.16813</td>
      <td>Entire home/apt</td>
      <td>150</td>
      <td>...</td>
      <td>5</td>
      <td>NaN</td>
      <td>Rental unit in London</td>
      <td>4.80</td>
      <td>1</td>
      <td>1 bed</td>
      <td>1 bath</td>
      <td>.80</td>
      <td>4</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>92644</td>
      <td>Rental unit in Earlsfield · ★4.57 · 1 bedroom ...</td>
      <td>498201</td>
      <td>Dee Dee</td>
      <td>NaN</td>
      <td>Wandsworth</td>
      <td>51.44201</td>
      <td>-0.18739</td>
      <td>Private room</td>
      <td>42</td>
      <td>...</td>
      <td>9</td>
      <td>NaN</td>
      <td>Rental unit in Earlsfield</td>
      <td>4.57</td>
      <td>1</td>
      <td>2 beds</td>
      <td>1.5 shared baths</td>
      <td>.57</td>
      <td>4</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>17402</td>
      <td>Rental unit in London · ★4.76 · 3 bedrooms · 3...</td>
      <td>67564</td>
      <td>Liz</td>
      <td>NaN</td>
      <td>Westminster</td>
      <td>51.52195</td>
      <td>-0.14094</td>
      <td>Entire home/apt</td>
      <td>476</td>
      <td>...</td>
      <td>4</td>
      <td>NaN</td>
      <td>Rental unit in London</td>
      <td>4.76</td>
      <td>3</td>
      <td>3 beds</td>
      <td>2 baths</td>
      <td>.76</td>
      <td>4</td>
      <td>12.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>93015</td>
      <td>Rental unit in Hammersmith · ★4.82 · 2 bedroom...</td>
      <td>499704</td>
      <td>Sarah</td>
      <td>NaN</td>
      <td>Hammersmith and Fulham</td>
      <td>51.49993</td>
      <td>-0.21707</td>
      <td>Entire home/apt</td>
      <td>175</td>
      <td>...</td>
      <td>2</td>
      <td>NaN</td>
      <td>Rental unit in Hammersmith</td>
      <td>4.82</td>
      <td>2</td>
      <td>3 beds</td>
      <td>1 bath</td>
      <td>.82</td>
      <td>4</td>
      <td>12.0</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 26 columns</p>
</div>




```python
#Perform similar action on Bedrooms,Beds and Bathrooms column
```


```python
#keeping only first 2 characters in 'Beds' column
```


```python
df['Beds'] = df['Beds'].str.slice(0, 2)
```


```python
df
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
      <th>id</th>
      <th>name</th>
      <th>host_id</th>
      <th>host_name</th>
      <th>neighbourhood_group</th>
      <th>neighbourhood</th>
      <th>latitude</th>
      <th>longitude</th>
      <th>room_type</th>
      <th>price</th>
      <th>...</th>
      <th>number_of_reviews_ltm</th>
      <th>license</th>
      <th>Property_Name</th>
      <th>Property_Rating</th>
      <th>Bedrooms</th>
      <th>Beds</th>
      <th>Bathrooms</th>
      <th>New_Property_Rating</th>
      <th>Property_Rating_Length</th>
      <th>Bedroom_Length</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>13913</td>
      <td>Rental unit in Islington · ★4.80 · 1 bedroom ·...</td>
      <td>54730</td>
      <td>Alina</td>
      <td>NaN</td>
      <td>Islington</td>
      <td>51.568610</td>
      <td>-0.112700</td>
      <td>Private room</td>
      <td>79</td>
      <td>...</td>
      <td>11</td>
      <td>NaN</td>
      <td>Rental unit in Islington</td>
      <td>4.80</td>
      <td>1</td>
      <td>1</td>
      <td>1 shared bath</td>
      <td>.80</td>
      <td>4</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15400</td>
      <td>Rental unit in London · ★4.80 · 1 bedroom · 1 ...</td>
      <td>60302</td>
      <td>Philippa</td>
      <td>NaN</td>
      <td>Kensington and Chelsea</td>
      <td>51.487800</td>
      <td>-0.168130</td>
      <td>Entire home/apt</td>
      <td>150</td>
      <td>...</td>
      <td>5</td>
      <td>NaN</td>
      <td>Rental unit in London</td>
      <td>4.80</td>
      <td>1</td>
      <td>1</td>
      <td>1 bath</td>
      <td>.80</td>
      <td>4</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>92644</td>
      <td>Rental unit in Earlsfield · ★4.57 · 1 bedroom ...</td>
      <td>498201</td>
      <td>Dee Dee</td>
      <td>NaN</td>
      <td>Wandsworth</td>
      <td>51.442010</td>
      <td>-0.187390</td>
      <td>Private room</td>
      <td>42</td>
      <td>...</td>
      <td>9</td>
      <td>NaN</td>
      <td>Rental unit in Earlsfield</td>
      <td>4.57</td>
      <td>1</td>
      <td>2</td>
      <td>1.5 shared baths</td>
      <td>.57</td>
      <td>4</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>17402</td>
      <td>Rental unit in London · ★4.76 · 3 bedrooms · 3...</td>
      <td>67564</td>
      <td>Liz</td>
      <td>NaN</td>
      <td>Westminster</td>
      <td>51.521950</td>
      <td>-0.140940</td>
      <td>Entire home/apt</td>
      <td>476</td>
      <td>...</td>
      <td>4</td>
      <td>NaN</td>
      <td>Rental unit in London</td>
      <td>4.76</td>
      <td>3</td>
      <td>3</td>
      <td>2 baths</td>
      <td>.76</td>
      <td>4</td>
      <td>12.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>93015</td>
      <td>Rental unit in Hammersmith · ★4.82 · 2 bedroom...</td>
      <td>499704</td>
      <td>Sarah</td>
      <td>NaN</td>
      <td>Hammersmith and Fulham</td>
      <td>51.499930</td>
      <td>-0.217070</td>
      <td>Entire home/apt</td>
      <td>175</td>
      <td>...</td>
      <td>2</td>
      <td>NaN</td>
      <td>Rental unit in Hammersmith</td>
      <td>4.82</td>
      <td>2</td>
      <td>3</td>
      <td>1 bath</td>
      <td>.82</td>
      <td>4</td>
      <td>12.0</td>
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
      <th>87942</th>
      <td>973781286754517228</td>
      <td>Rental unit in Greater London · ★New · 1 bedro...</td>
      <td>498408783</td>
      <td>Sal</td>
      <td>NaN</td>
      <td>Westminster</td>
      <td>51.514860</td>
      <td>-0.135980</td>
      <td>Entire home/apt</td>
      <td>275</td>
      <td>...</td>
      <td>0</td>
      <td>NaN</td>
      <td>Rental unit in Greater London</td>
      <td>New</td>
      <td>1</td>
      <td>2</td>
      <td>1 bath</td>
      <td>New</td>
      <td>3</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>87943</th>
      <td>973801695874775338</td>
      <td>Rental unit in Greater London · ★New · 1 bedro...</td>
      <td>36645347</td>
      <td>Josie</td>
      <td>NaN</td>
      <td>Southwark</td>
      <td>51.459042</td>
      <td>-0.055458</td>
      <td>Entire home/apt</td>
      <td>145</td>
      <td>...</td>
      <td>0</td>
      <td>NaN</td>
      <td>Rental unit in Greater London</td>
      <td>New</td>
      <td>1</td>
      <td>1</td>
      <td>1 bath</td>
      <td>New</td>
      <td>3</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>87944</th>
      <td>973811685656289740</td>
      <td>Home in Greater London · ★New · 1 bedroom · 5 ...</td>
      <td>340514057</td>
      <td>Mal</td>
      <td>NaN</td>
      <td>Merton</td>
      <td>51.406100</td>
      <td>-0.236126</td>
      <td>Private room</td>
      <td>160</td>
      <td>...</td>
      <td>0</td>
      <td>NaN</td>
      <td>Home in Greater London</td>
      <td>New</td>
      <td>1</td>
      <td>5</td>
      <td>2 shared baths</td>
      <td>New</td>
      <td>3</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>87945</th>
      <td>973882998775927897</td>
      <td>Home in Greater London · ★New · 5 bedrooms · 5...</td>
      <td>439074505</td>
      <td>Travelnest</td>
      <td>NaN</td>
      <td>Hounslow</td>
      <td>51.450997</td>
      <td>-0.444319</td>
      <td>Entire home/apt</td>
      <td>680</td>
      <td>...</td>
      <td>0</td>
      <td>NaN</td>
      <td>Home in Greater London</td>
      <td>New</td>
      <td>5</td>
      <td>5</td>
      <td>1 bath</td>
      <td>New</td>
      <td>3</td>
      <td>12.0</td>
    </tr>
    <tr>
      <th>87946</th>
      <td>973895808066047620</td>
      <td>Rental unit in Greater London · ★New · 2 bedro...</td>
      <td>475112423</td>
      <td>Lea</td>
      <td>NaN</td>
      <td>City of London</td>
      <td>51.515970</td>
      <td>-0.111342</td>
      <td>Entire home/apt</td>
      <td>170</td>
      <td>...</td>
      <td>0</td>
      <td>NaN</td>
      <td>Rental unit in Greater London</td>
      <td>New</td>
      <td>2</td>
      <td>3</td>
      <td>1 bath</td>
      <td>New</td>
      <td>3</td>
      <td>12.0</td>
    </tr>
  </tbody>
</table>
<p>87947 rows × 26 columns</p>
</div>




```python
#Different approach for column 'Bathrooms' as column can have .5 bathroom and 
#hence can't filter out required data with only index

#only including first 4 characters regardless of alphabet may be included in few rows and
#assuming whitespace in beginning
```


```python
df['New_Bathrooms'] = df['Bathrooms'].str.slice(0,4)
```


```python
df
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
      <th>id</th>
      <th>name</th>
      <th>host_id</th>
      <th>host_name</th>
      <th>neighbourhood_group</th>
      <th>neighbourhood</th>
      <th>latitude</th>
      <th>longitude</th>
      <th>room_type</th>
      <th>price</th>
      <th>...</th>
      <th>license</th>
      <th>Property_Name</th>
      <th>Property_Rating</th>
      <th>Bedrooms</th>
      <th>Beds</th>
      <th>Bathrooms</th>
      <th>New_Property_Rating</th>
      <th>Property_Rating_Length</th>
      <th>Bedroom_Length</th>
      <th>New_Bathrooms</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>13913</td>
      <td>Rental unit in Islington · ★4.80 · 1 bedroom ·...</td>
      <td>54730</td>
      <td>Alina</td>
      <td>NaN</td>
      <td>Islington</td>
      <td>51.568610</td>
      <td>-0.112700</td>
      <td>Private room</td>
      <td>79</td>
      <td>...</td>
      <td>NaN</td>
      <td>Rental unit in Islington</td>
      <td>4.80</td>
      <td>1</td>
      <td>1</td>
      <td>1 shared bath</td>
      <td>.80</td>
      <td>4</td>
      <td>11.0</td>
      <td>1 s</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15400</td>
      <td>Rental unit in London · ★4.80 · 1 bedroom · 1 ...</td>
      <td>60302</td>
      <td>Philippa</td>
      <td>NaN</td>
      <td>Kensington and Chelsea</td>
      <td>51.487800</td>
      <td>-0.168130</td>
      <td>Entire home/apt</td>
      <td>150</td>
      <td>...</td>
      <td>NaN</td>
      <td>Rental unit in London</td>
      <td>4.80</td>
      <td>1</td>
      <td>1</td>
      <td>1 bath</td>
      <td>.80</td>
      <td>4</td>
      <td>11.0</td>
      <td>1 b</td>
    </tr>
    <tr>
      <th>2</th>
      <td>92644</td>
      <td>Rental unit in Earlsfield · ★4.57 · 1 bedroom ...</td>
      <td>498201</td>
      <td>Dee Dee</td>
      <td>NaN</td>
      <td>Wandsworth</td>
      <td>51.442010</td>
      <td>-0.187390</td>
      <td>Private room</td>
      <td>42</td>
      <td>...</td>
      <td>NaN</td>
      <td>Rental unit in Earlsfield</td>
      <td>4.57</td>
      <td>1</td>
      <td>2</td>
      <td>1.5 shared baths</td>
      <td>.57</td>
      <td>4</td>
      <td>11.0</td>
      <td>1.5</td>
    </tr>
    <tr>
      <th>3</th>
      <td>17402</td>
      <td>Rental unit in London · ★4.76 · 3 bedrooms · 3...</td>
      <td>67564</td>
      <td>Liz</td>
      <td>NaN</td>
      <td>Westminster</td>
      <td>51.521950</td>
      <td>-0.140940</td>
      <td>Entire home/apt</td>
      <td>476</td>
      <td>...</td>
      <td>NaN</td>
      <td>Rental unit in London</td>
      <td>4.76</td>
      <td>3</td>
      <td>3</td>
      <td>2 baths</td>
      <td>.76</td>
      <td>4</td>
      <td>12.0</td>
      <td>2 b</td>
    </tr>
    <tr>
      <th>4</th>
      <td>93015</td>
      <td>Rental unit in Hammersmith · ★4.82 · 2 bedroom...</td>
      <td>499704</td>
      <td>Sarah</td>
      <td>NaN</td>
      <td>Hammersmith and Fulham</td>
      <td>51.499930</td>
      <td>-0.217070</td>
      <td>Entire home/apt</td>
      <td>175</td>
      <td>...</td>
      <td>NaN</td>
      <td>Rental unit in Hammersmith</td>
      <td>4.82</td>
      <td>2</td>
      <td>3</td>
      <td>1 bath</td>
      <td>.82</td>
      <td>4</td>
      <td>12.0</td>
      <td>1 b</td>
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
      <th>87942</th>
      <td>973781286754517228</td>
      <td>Rental unit in Greater London · ★New · 1 bedro...</td>
      <td>498408783</td>
      <td>Sal</td>
      <td>NaN</td>
      <td>Westminster</td>
      <td>51.514860</td>
      <td>-0.135980</td>
      <td>Entire home/apt</td>
      <td>275</td>
      <td>...</td>
      <td>NaN</td>
      <td>Rental unit in Greater London</td>
      <td>New</td>
      <td>1</td>
      <td>2</td>
      <td>1 bath</td>
      <td>New</td>
      <td>3</td>
      <td>11.0</td>
      <td>1 b</td>
    </tr>
    <tr>
      <th>87943</th>
      <td>973801695874775338</td>
      <td>Rental unit in Greater London · ★New · 1 bedro...</td>
      <td>36645347</td>
      <td>Josie</td>
      <td>NaN</td>
      <td>Southwark</td>
      <td>51.459042</td>
      <td>-0.055458</td>
      <td>Entire home/apt</td>
      <td>145</td>
      <td>...</td>
      <td>NaN</td>
      <td>Rental unit in Greater London</td>
      <td>New</td>
      <td>1</td>
      <td>1</td>
      <td>1 bath</td>
      <td>New</td>
      <td>3</td>
      <td>11.0</td>
      <td>1 b</td>
    </tr>
    <tr>
      <th>87944</th>
      <td>973811685656289740</td>
      <td>Home in Greater London · ★New · 1 bedroom · 5 ...</td>
      <td>340514057</td>
      <td>Mal</td>
      <td>NaN</td>
      <td>Merton</td>
      <td>51.406100</td>
      <td>-0.236126</td>
      <td>Private room</td>
      <td>160</td>
      <td>...</td>
      <td>NaN</td>
      <td>Home in Greater London</td>
      <td>New</td>
      <td>1</td>
      <td>5</td>
      <td>2 shared baths</td>
      <td>New</td>
      <td>3</td>
      <td>11.0</td>
      <td>2 s</td>
    </tr>
    <tr>
      <th>87945</th>
      <td>973882998775927897</td>
      <td>Home in Greater London · ★New · 5 bedrooms · 5...</td>
      <td>439074505</td>
      <td>Travelnest</td>
      <td>NaN</td>
      <td>Hounslow</td>
      <td>51.450997</td>
      <td>-0.444319</td>
      <td>Entire home/apt</td>
      <td>680</td>
      <td>...</td>
      <td>NaN</td>
      <td>Home in Greater London</td>
      <td>New</td>
      <td>5</td>
      <td>5</td>
      <td>1 bath</td>
      <td>New</td>
      <td>3</td>
      <td>12.0</td>
      <td>1 b</td>
    </tr>
    <tr>
      <th>87946</th>
      <td>973895808066047620</td>
      <td>Rental unit in Greater London · ★New · 2 bedro...</td>
      <td>475112423</td>
      <td>Lea</td>
      <td>NaN</td>
      <td>City of London</td>
      <td>51.515970</td>
      <td>-0.111342</td>
      <td>Entire home/apt</td>
      <td>170</td>
      <td>...</td>
      <td>NaN</td>
      <td>Rental unit in Greater London</td>
      <td>New</td>
      <td>2</td>
      <td>3</td>
      <td>1 bath</td>
      <td>New</td>
      <td>3</td>
      <td>12.0</td>
      <td>1 b</td>
    </tr>
  </tbody>
</table>
<p>87947 rows × 27 columns</p>
</div>




```python
#Removing any characters except "." and numbers in the column 
```


```python
df['New_Bathrooms'] = df['New_Bathrooms'].str.replace(r'[^0-9.]', '', regex=True)

```


```python
df
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
      <th>id</th>
      <th>name</th>
      <th>host_id</th>
      <th>host_name</th>
      <th>neighbourhood_group</th>
      <th>neighbourhood</th>
      <th>latitude</th>
      <th>longitude</th>
      <th>room_type</th>
      <th>price</th>
      <th>...</th>
      <th>license</th>
      <th>Property_Name</th>
      <th>Property_Rating</th>
      <th>Bedrooms</th>
      <th>Beds</th>
      <th>Bathrooms</th>
      <th>New_Property_Rating</th>
      <th>Property_Rating_Length</th>
      <th>Bedroom_Length</th>
      <th>New_Bathrooms</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>13913</td>
      <td>Rental unit in Islington · ★4.80 · 1 bedroom ·...</td>
      <td>54730</td>
      <td>Alina</td>
      <td>NaN</td>
      <td>Islington</td>
      <td>51.568610</td>
      <td>-0.112700</td>
      <td>Private room</td>
      <td>79</td>
      <td>...</td>
      <td>NaN</td>
      <td>Rental unit in Islington</td>
      <td>4.80</td>
      <td>1</td>
      <td>1</td>
      <td>1 shared bath</td>
      <td>.80</td>
      <td>4</td>
      <td>11.0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15400</td>
      <td>Rental unit in London · ★4.80 · 1 bedroom · 1 ...</td>
      <td>60302</td>
      <td>Philippa</td>
      <td>NaN</td>
      <td>Kensington and Chelsea</td>
      <td>51.487800</td>
      <td>-0.168130</td>
      <td>Entire home/apt</td>
      <td>150</td>
      <td>...</td>
      <td>NaN</td>
      <td>Rental unit in London</td>
      <td>4.80</td>
      <td>1</td>
      <td>1</td>
      <td>1 bath</td>
      <td>.80</td>
      <td>4</td>
      <td>11.0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>92644</td>
      <td>Rental unit in Earlsfield · ★4.57 · 1 bedroom ...</td>
      <td>498201</td>
      <td>Dee Dee</td>
      <td>NaN</td>
      <td>Wandsworth</td>
      <td>51.442010</td>
      <td>-0.187390</td>
      <td>Private room</td>
      <td>42</td>
      <td>...</td>
      <td>NaN</td>
      <td>Rental unit in Earlsfield</td>
      <td>4.57</td>
      <td>1</td>
      <td>2</td>
      <td>1.5 shared baths</td>
      <td>.57</td>
      <td>4</td>
      <td>11.0</td>
      <td>1.5</td>
    </tr>
    <tr>
      <th>3</th>
      <td>17402</td>
      <td>Rental unit in London · ★4.76 · 3 bedrooms · 3...</td>
      <td>67564</td>
      <td>Liz</td>
      <td>NaN</td>
      <td>Westminster</td>
      <td>51.521950</td>
      <td>-0.140940</td>
      <td>Entire home/apt</td>
      <td>476</td>
      <td>...</td>
      <td>NaN</td>
      <td>Rental unit in London</td>
      <td>4.76</td>
      <td>3</td>
      <td>3</td>
      <td>2 baths</td>
      <td>.76</td>
      <td>4</td>
      <td>12.0</td>
      <td>2</td>
    </tr>
    <tr>
      <th>4</th>
      <td>93015</td>
      <td>Rental unit in Hammersmith · ★4.82 · 2 bedroom...</td>
      <td>499704</td>
      <td>Sarah</td>
      <td>NaN</td>
      <td>Hammersmith and Fulham</td>
      <td>51.499930</td>
      <td>-0.217070</td>
      <td>Entire home/apt</td>
      <td>175</td>
      <td>...</td>
      <td>NaN</td>
      <td>Rental unit in Hammersmith</td>
      <td>4.82</td>
      <td>2</td>
      <td>3</td>
      <td>1 bath</td>
      <td>.82</td>
      <td>4</td>
      <td>12.0</td>
      <td>1</td>
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
      <th>87942</th>
      <td>973781286754517228</td>
      <td>Rental unit in Greater London · ★New · 1 bedro...</td>
      <td>498408783</td>
      <td>Sal</td>
      <td>NaN</td>
      <td>Westminster</td>
      <td>51.514860</td>
      <td>-0.135980</td>
      <td>Entire home/apt</td>
      <td>275</td>
      <td>...</td>
      <td>NaN</td>
      <td>Rental unit in Greater London</td>
      <td>New</td>
      <td>1</td>
      <td>2</td>
      <td>1 bath</td>
      <td>New</td>
      <td>3</td>
      <td>11.0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>87943</th>
      <td>973801695874775338</td>
      <td>Rental unit in Greater London · ★New · 1 bedro...</td>
      <td>36645347</td>
      <td>Josie</td>
      <td>NaN</td>
      <td>Southwark</td>
      <td>51.459042</td>
      <td>-0.055458</td>
      <td>Entire home/apt</td>
      <td>145</td>
      <td>...</td>
      <td>NaN</td>
      <td>Rental unit in Greater London</td>
      <td>New</td>
      <td>1</td>
      <td>1</td>
      <td>1 bath</td>
      <td>New</td>
      <td>3</td>
      <td>11.0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>87944</th>
      <td>973811685656289740</td>
      <td>Home in Greater London · ★New · 1 bedroom · 5 ...</td>
      <td>340514057</td>
      <td>Mal</td>
      <td>NaN</td>
      <td>Merton</td>
      <td>51.406100</td>
      <td>-0.236126</td>
      <td>Private room</td>
      <td>160</td>
      <td>...</td>
      <td>NaN</td>
      <td>Home in Greater London</td>
      <td>New</td>
      <td>1</td>
      <td>5</td>
      <td>2 shared baths</td>
      <td>New</td>
      <td>3</td>
      <td>11.0</td>
      <td>2</td>
    </tr>
    <tr>
      <th>87945</th>
      <td>973882998775927897</td>
      <td>Home in Greater London · ★New · 5 bedrooms · 5...</td>
      <td>439074505</td>
      <td>Travelnest</td>
      <td>NaN</td>
      <td>Hounslow</td>
      <td>51.450997</td>
      <td>-0.444319</td>
      <td>Entire home/apt</td>
      <td>680</td>
      <td>...</td>
      <td>NaN</td>
      <td>Home in Greater London</td>
      <td>New</td>
      <td>5</td>
      <td>5</td>
      <td>1 bath</td>
      <td>New</td>
      <td>3</td>
      <td>12.0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>87946</th>
      <td>973895808066047620</td>
      <td>Rental unit in Greater London · ★New · 2 bedro...</td>
      <td>475112423</td>
      <td>Lea</td>
      <td>NaN</td>
      <td>City of London</td>
      <td>51.515970</td>
      <td>-0.111342</td>
      <td>Entire home/apt</td>
      <td>170</td>
      <td>...</td>
      <td>NaN</td>
      <td>Rental unit in Greater London</td>
      <td>New</td>
      <td>2</td>
      <td>3</td>
      <td>1 bath</td>
      <td>New</td>
      <td>3</td>
      <td>12.0</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
<p>87947 rows × 27 columns</p>
</div>




```python
df = df.drop('Bathrooms', axis=1)

```


```python
df
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
      <th>id</th>
      <th>name</th>
      <th>host_id</th>
      <th>host_name</th>
      <th>neighbourhood_group</th>
      <th>neighbourhood</th>
      <th>latitude</th>
      <th>longitude</th>
      <th>room_type</th>
      <th>price</th>
      <th>...</th>
      <th>number_of_reviews_ltm</th>
      <th>license</th>
      <th>Property_Name</th>
      <th>Property_Rating</th>
      <th>Bedrooms</th>
      <th>Beds</th>
      <th>New_Property_Rating</th>
      <th>Property_Rating_Length</th>
      <th>Bedroom_Length</th>
      <th>New_Bathrooms</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>13913</td>
      <td>Rental unit in Islington · ★4.80 · 1 bedroom ·...</td>
      <td>54730</td>
      <td>Alina</td>
      <td>NaN</td>
      <td>Islington</td>
      <td>51.568610</td>
      <td>-0.112700</td>
      <td>Private room</td>
      <td>79</td>
      <td>...</td>
      <td>11</td>
      <td>NaN</td>
      <td>Rental unit in Islington</td>
      <td>4.80</td>
      <td>1</td>
      <td>1</td>
      <td>.80</td>
      <td>4</td>
      <td>11.0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15400</td>
      <td>Rental unit in London · ★4.80 · 1 bedroom · 1 ...</td>
      <td>60302</td>
      <td>Philippa</td>
      <td>NaN</td>
      <td>Kensington and Chelsea</td>
      <td>51.487800</td>
      <td>-0.168130</td>
      <td>Entire home/apt</td>
      <td>150</td>
      <td>...</td>
      <td>5</td>
      <td>NaN</td>
      <td>Rental unit in London</td>
      <td>4.80</td>
      <td>1</td>
      <td>1</td>
      <td>.80</td>
      <td>4</td>
      <td>11.0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>92644</td>
      <td>Rental unit in Earlsfield · ★4.57 · 1 bedroom ...</td>
      <td>498201</td>
      <td>Dee Dee</td>
      <td>NaN</td>
      <td>Wandsworth</td>
      <td>51.442010</td>
      <td>-0.187390</td>
      <td>Private room</td>
      <td>42</td>
      <td>...</td>
      <td>9</td>
      <td>NaN</td>
      <td>Rental unit in Earlsfield</td>
      <td>4.57</td>
      <td>1</td>
      <td>2</td>
      <td>.57</td>
      <td>4</td>
      <td>11.0</td>
      <td>1.5</td>
    </tr>
    <tr>
      <th>3</th>
      <td>17402</td>
      <td>Rental unit in London · ★4.76 · 3 bedrooms · 3...</td>
      <td>67564</td>
      <td>Liz</td>
      <td>NaN</td>
      <td>Westminster</td>
      <td>51.521950</td>
      <td>-0.140940</td>
      <td>Entire home/apt</td>
      <td>476</td>
      <td>...</td>
      <td>4</td>
      <td>NaN</td>
      <td>Rental unit in London</td>
      <td>4.76</td>
      <td>3</td>
      <td>3</td>
      <td>.76</td>
      <td>4</td>
      <td>12.0</td>
      <td>2</td>
    </tr>
    <tr>
      <th>4</th>
      <td>93015</td>
      <td>Rental unit in Hammersmith · ★4.82 · 2 bedroom...</td>
      <td>499704</td>
      <td>Sarah</td>
      <td>NaN</td>
      <td>Hammersmith and Fulham</td>
      <td>51.499930</td>
      <td>-0.217070</td>
      <td>Entire home/apt</td>
      <td>175</td>
      <td>...</td>
      <td>2</td>
      <td>NaN</td>
      <td>Rental unit in Hammersmith</td>
      <td>4.82</td>
      <td>2</td>
      <td>3</td>
      <td>.82</td>
      <td>4</td>
      <td>12.0</td>
      <td>1</td>
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
      <th>87942</th>
      <td>973781286754517228</td>
      <td>Rental unit in Greater London · ★New · 1 bedro...</td>
      <td>498408783</td>
      <td>Sal</td>
      <td>NaN</td>
      <td>Westminster</td>
      <td>51.514860</td>
      <td>-0.135980</td>
      <td>Entire home/apt</td>
      <td>275</td>
      <td>...</td>
      <td>0</td>
      <td>NaN</td>
      <td>Rental unit in Greater London</td>
      <td>New</td>
      <td>1</td>
      <td>2</td>
      <td>New</td>
      <td>3</td>
      <td>11.0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>87943</th>
      <td>973801695874775338</td>
      <td>Rental unit in Greater London · ★New · 1 bedro...</td>
      <td>36645347</td>
      <td>Josie</td>
      <td>NaN</td>
      <td>Southwark</td>
      <td>51.459042</td>
      <td>-0.055458</td>
      <td>Entire home/apt</td>
      <td>145</td>
      <td>...</td>
      <td>0</td>
      <td>NaN</td>
      <td>Rental unit in Greater London</td>
      <td>New</td>
      <td>1</td>
      <td>1</td>
      <td>New</td>
      <td>3</td>
      <td>11.0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>87944</th>
      <td>973811685656289740</td>
      <td>Home in Greater London · ★New · 1 bedroom · 5 ...</td>
      <td>340514057</td>
      <td>Mal</td>
      <td>NaN</td>
      <td>Merton</td>
      <td>51.406100</td>
      <td>-0.236126</td>
      <td>Private room</td>
      <td>160</td>
      <td>...</td>
      <td>0</td>
      <td>NaN</td>
      <td>Home in Greater London</td>
      <td>New</td>
      <td>1</td>
      <td>5</td>
      <td>New</td>
      <td>3</td>
      <td>11.0</td>
      <td>2</td>
    </tr>
    <tr>
      <th>87945</th>
      <td>973882998775927897</td>
      <td>Home in Greater London · ★New · 5 bedrooms · 5...</td>
      <td>439074505</td>
      <td>Travelnest</td>
      <td>NaN</td>
      <td>Hounslow</td>
      <td>51.450997</td>
      <td>-0.444319</td>
      <td>Entire home/apt</td>
      <td>680</td>
      <td>...</td>
      <td>0</td>
      <td>NaN</td>
      <td>Home in Greater London</td>
      <td>New</td>
      <td>5</td>
      <td>5</td>
      <td>New</td>
      <td>3</td>
      <td>12.0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>87946</th>
      <td>973895808066047620</td>
      <td>Rental unit in Greater London · ★New · 2 bedro...</td>
      <td>475112423</td>
      <td>Lea</td>
      <td>NaN</td>
      <td>City of London</td>
      <td>51.515970</td>
      <td>-0.111342</td>
      <td>Entire home/apt</td>
      <td>170</td>
      <td>...</td>
      <td>0</td>
      <td>NaN</td>
      <td>Rental unit in Greater London</td>
      <td>New</td>
      <td>2</td>
      <td>3</td>
      <td>New</td>
      <td>3</td>
      <td>12.0</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
<p>87947 rows × 26 columns</p>
</div>




```python
df = df.rename(columns={'New_Bathrooms': 'Bathrooms'})
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
      <th>id</th>
      <th>name</th>
      <th>host_id</th>
      <th>host_name</th>
      <th>neighbourhood_group</th>
      <th>neighbourhood</th>
      <th>latitude</th>
      <th>longitude</th>
      <th>room_type</th>
      <th>price</th>
      <th>...</th>
      <th>number_of_reviews_ltm</th>
      <th>license</th>
      <th>Property_Name</th>
      <th>Property_Rating</th>
      <th>Bedrooms</th>
      <th>Beds</th>
      <th>New_Property_Rating</th>
      <th>Property_Rating_Length</th>
      <th>Bedroom_Length</th>
      <th>Bathrooms</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>13913</td>
      <td>Rental unit in Islington · ★4.80 · 1 bedroom ·...</td>
      <td>54730</td>
      <td>Alina</td>
      <td>NaN</td>
      <td>Islington</td>
      <td>51.56861</td>
      <td>-0.11270</td>
      <td>Private room</td>
      <td>79</td>
      <td>...</td>
      <td>11</td>
      <td>NaN</td>
      <td>Rental unit in Islington</td>
      <td>4.80</td>
      <td>1</td>
      <td>1</td>
      <td>.80</td>
      <td>4</td>
      <td>11.0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15400</td>
      <td>Rental unit in London · ★4.80 · 1 bedroom · 1 ...</td>
      <td>60302</td>
      <td>Philippa</td>
      <td>NaN</td>
      <td>Kensington and Chelsea</td>
      <td>51.48780</td>
      <td>-0.16813</td>
      <td>Entire home/apt</td>
      <td>150</td>
      <td>...</td>
      <td>5</td>
      <td>NaN</td>
      <td>Rental unit in London</td>
      <td>4.80</td>
      <td>1</td>
      <td>1</td>
      <td>.80</td>
      <td>4</td>
      <td>11.0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>92644</td>
      <td>Rental unit in Earlsfield · ★4.57 · 1 bedroom ...</td>
      <td>498201</td>
      <td>Dee Dee</td>
      <td>NaN</td>
      <td>Wandsworth</td>
      <td>51.44201</td>
      <td>-0.18739</td>
      <td>Private room</td>
      <td>42</td>
      <td>...</td>
      <td>9</td>
      <td>NaN</td>
      <td>Rental unit in Earlsfield</td>
      <td>4.57</td>
      <td>1</td>
      <td>2</td>
      <td>.57</td>
      <td>4</td>
      <td>11.0</td>
      <td>1.5</td>
    </tr>
    <tr>
      <th>3</th>
      <td>17402</td>
      <td>Rental unit in London · ★4.76 · 3 bedrooms · 3...</td>
      <td>67564</td>
      <td>Liz</td>
      <td>NaN</td>
      <td>Westminster</td>
      <td>51.52195</td>
      <td>-0.14094</td>
      <td>Entire home/apt</td>
      <td>476</td>
      <td>...</td>
      <td>4</td>
      <td>NaN</td>
      <td>Rental unit in London</td>
      <td>4.76</td>
      <td>3</td>
      <td>3</td>
      <td>.76</td>
      <td>4</td>
      <td>12.0</td>
      <td>2</td>
    </tr>
    <tr>
      <th>4</th>
      <td>93015</td>
      <td>Rental unit in Hammersmith · ★4.82 · 2 bedroom...</td>
      <td>499704</td>
      <td>Sarah</td>
      <td>NaN</td>
      <td>Hammersmith and Fulham</td>
      <td>51.49993</td>
      <td>-0.21707</td>
      <td>Entire home/apt</td>
      <td>175</td>
      <td>...</td>
      <td>2</td>
      <td>NaN</td>
      <td>Rental unit in Hammersmith</td>
      <td>4.82</td>
      <td>2</td>
      <td>3</td>
      <td>.82</td>
      <td>4</td>
      <td>12.0</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 26 columns</p>
</div>




```python
#Dropping all unrequired columns to clean up the table

#Dropping "name" , "neighbourhood_group" , "license" ,
#"New_Property_Rating" ,"Property_Rating_Length" , "Bedroom_Length"
```


```python
columns_to_drop = ['name', 'neighbourhood_group', 'license', 'New_Property_Rating', 'Property_Rating_Length', 'Bedroom_Length']

```


```python
df = df.drop(columns=columns_to_drop, axis=1)
```


```python
df
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
      <th>id</th>
      <th>host_id</th>
      <th>host_name</th>
      <th>neighbourhood</th>
      <th>latitude</th>
      <th>longitude</th>
      <th>room_type</th>
      <th>price</th>
      <th>minimum_nights</th>
      <th>number_of_reviews</th>
      <th>last_review</th>
      <th>reviews_per_month</th>
      <th>calculated_host_listings_count</th>
      <th>availability_365</th>
      <th>number_of_reviews_ltm</th>
      <th>Property_Name</th>
      <th>Property_Rating</th>
      <th>Bedrooms</th>
      <th>Beds</th>
      <th>Bathrooms</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>13913</td>
      <td>54730</td>
      <td>Alina</td>
      <td>Islington</td>
      <td>51.568610</td>
      <td>-0.112700</td>
      <td>Private room</td>
      <td>79</td>
      <td>1</td>
      <td>41</td>
      <td>2022-12-11</td>
      <td>0.26</td>
      <td>2</td>
      <td>360</td>
      <td>11</td>
      <td>Rental unit in Islington</td>
      <td>4.80</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15400</td>
      <td>60302</td>
      <td>Philippa</td>
      <td>Kensington and Chelsea</td>
      <td>51.487800</td>
      <td>-0.168130</td>
      <td>Entire home/apt</td>
      <td>150</td>
      <td>7</td>
      <td>94</td>
      <td>2023-05-01</td>
      <td>0.56</td>
      <td>1</td>
      <td>73</td>
      <td>5</td>
      <td>Rental unit in London</td>
      <td>4.80</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>92644</td>
      <td>498201</td>
      <td>Dee Dee</td>
      <td>Wandsworth</td>
      <td>51.442010</td>
      <td>-0.187390</td>
      <td>Private room</td>
      <td>42</td>
      <td>2</td>
      <td>216</td>
      <td>2022-10-29</td>
      <td>1.45</td>
      <td>1</td>
      <td>217</td>
      <td>9</td>
      <td>Rental unit in Earlsfield</td>
      <td>4.57</td>
      <td>1</td>
      <td>2</td>
      <td>1.5</td>
    </tr>
    <tr>
      <th>3</th>
      <td>17402</td>
      <td>67564</td>
      <td>Liz</td>
      <td>Westminster</td>
      <td>51.521950</td>
      <td>-0.140940</td>
      <td>Entire home/apt</td>
      <td>476</td>
      <td>3</td>
      <td>54</td>
      <td>2022-11-19</td>
      <td>0.36</td>
      <td>9</td>
      <td>300</td>
      <td>4</td>
      <td>Rental unit in London</td>
      <td>4.76</td>
      <td>3</td>
      <td>3</td>
      <td>2</td>
    </tr>
    <tr>
      <th>4</th>
      <td>93015</td>
      <td>499704</td>
      <td>Sarah</td>
      <td>Hammersmith and Fulham</td>
      <td>51.499930</td>
      <td>-0.217070</td>
      <td>Entire home/apt</td>
      <td>175</td>
      <td>5</td>
      <td>38</td>
      <td>2022-09-30</td>
      <td>0.27</td>
      <td>1</td>
      <td>40</td>
      <td>2</td>
      <td>Rental unit in Hammersmith</td>
      <td>4.82</td>
      <td>2</td>
      <td>3</td>
      <td>1</td>
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
    </tr>
    <tr>
      <th>87942</th>
      <td>973781286754517228</td>
      <td>498408783</td>
      <td>Sal</td>
      <td>Westminster</td>
      <td>51.514860</td>
      <td>-0.135980</td>
      <td>Entire home/apt</td>
      <td>275</td>
      <td>2</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2</td>
      <td>239</td>
      <td>0</td>
      <td>Rental unit in Greater London</td>
      <td>New</td>
      <td>1</td>
      <td>2</td>
      <td>1</td>
    </tr>
    <tr>
      <th>87943</th>
      <td>973801695874775338</td>
      <td>36645347</td>
      <td>Josie</td>
      <td>Southwark</td>
      <td>51.459042</td>
      <td>-0.055458</td>
      <td>Entire home/apt</td>
      <td>145</td>
      <td>3</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1</td>
      <td>88</td>
      <td>0</td>
      <td>Rental unit in Greater London</td>
      <td>New</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>87944</th>
      <td>973811685656289740</td>
      <td>340514057</td>
      <td>Mal</td>
      <td>Merton</td>
      <td>51.406100</td>
      <td>-0.236126</td>
      <td>Private room</td>
      <td>160</td>
      <td>1</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1</td>
      <td>80</td>
      <td>0</td>
      <td>Home in Greater London</td>
      <td>New</td>
      <td>1</td>
      <td>5</td>
      <td>2</td>
    </tr>
    <tr>
      <th>87945</th>
      <td>973882998775927897</td>
      <td>439074505</td>
      <td>Travelnest</td>
      <td>Hounslow</td>
      <td>51.450997</td>
      <td>-0.444319</td>
      <td>Entire home/apt</td>
      <td>680</td>
      <td>1</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>170</td>
      <td>364</td>
      <td>0</td>
      <td>Home in Greater London</td>
      <td>New</td>
      <td>5</td>
      <td>5</td>
      <td>1</td>
    </tr>
    <tr>
      <th>87946</th>
      <td>973895808066047620</td>
      <td>475112423</td>
      <td>Lea</td>
      <td>City of London</td>
      <td>51.515970</td>
      <td>-0.111342</td>
      <td>Entire home/apt</td>
      <td>170</td>
      <td>1</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6</td>
      <td>297</td>
      <td>0</td>
      <td>Rental unit in Greater London</td>
      <td>New</td>
      <td>2</td>
      <td>3</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
<p>87947 rows × 20 columns</p>
</div>




```python
#Raw data has been transformed to pre processed data ready for analysis to be performed

#The new clean data is saved in a new csv file "new_listings"
```


```python
df.to_csv('/Users/gurudarshan/UOG/Projects/untitled folder/new_listings.csv', index=False)
```


```python

```
