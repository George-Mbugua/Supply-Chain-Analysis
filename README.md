```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

```


```python
df = pd.read_csv("supply_chain_dataset.csv")
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
      <th>Product type</th>
      <th>SKU</th>
      <th>Price</th>
      <th>Availability</th>
      <th>Number of products sold</th>
      <th>Revenue generated</th>
      <th>Customer demographics</th>
      <th>Stock levels</th>
      <th>Lead times</th>
      <th>Order quantities</th>
      <th>...</th>
      <th>Location</th>
      <th>Lead time</th>
      <th>Production volumes</th>
      <th>Manufacturing lead time</th>
      <th>Manufacturing costs</th>
      <th>Inspection results</th>
      <th>Defect rates</th>
      <th>Transportation modes</th>
      <th>Routes</th>
      <th>Costs</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>haircare</td>
      <td>SKU0</td>
      <td>69.808006</td>
      <td>55</td>
      <td>802</td>
      <td>8661.996792</td>
      <td>Non-binary</td>
      <td>58</td>
      <td>7</td>
      <td>96</td>
      <td>...</td>
      <td>Mumbai</td>
      <td>29</td>
      <td>215</td>
      <td>29</td>
      <td>46.279879</td>
      <td>Pending</td>
      <td>0.226410</td>
      <td>Road</td>
      <td>Route B</td>
      <td>187.752075</td>
    </tr>
    <tr>
      <th>1</th>
      <td>skincare</td>
      <td>SKU1</td>
      <td>14.843523</td>
      <td>95</td>
      <td>736</td>
      <td>7460.900065</td>
      <td>Female</td>
      <td>53</td>
      <td>30</td>
      <td>37</td>
      <td>...</td>
      <td>Mumbai</td>
      <td>23</td>
      <td>517</td>
      <td>30</td>
      <td>33.616769</td>
      <td>Pending</td>
      <td>4.854068</td>
      <td>Road</td>
      <td>Route B</td>
      <td>503.065579</td>
    </tr>
    <tr>
      <th>2</th>
      <td>haircare</td>
      <td>SKU2</td>
      <td>11.319683</td>
      <td>34</td>
      <td>8</td>
      <td>9577.749626</td>
      <td>Unknown</td>
      <td>1</td>
      <td>10</td>
      <td>88</td>
      <td>...</td>
      <td>Mumbai</td>
      <td>12</td>
      <td>971</td>
      <td>27</td>
      <td>30.688019</td>
      <td>Pending</td>
      <td>4.580593</td>
      <td>Air</td>
      <td>Route C</td>
      <td>141.920282</td>
    </tr>
    <tr>
      <th>3</th>
      <td>skincare</td>
      <td>SKU3</td>
      <td>61.163343</td>
      <td>68</td>
      <td>83</td>
      <td>7766.836426</td>
      <td>Non-binary</td>
      <td>23</td>
      <td>13</td>
      <td>59</td>
      <td>...</td>
      <td>Kolkata</td>
      <td>24</td>
      <td>937</td>
      <td>18</td>
      <td>35.624741</td>
      <td>Fail</td>
      <td>4.746649</td>
      <td>Rail</td>
      <td>Route A</td>
      <td>254.776159</td>
    </tr>
    <tr>
      <th>4</th>
      <td>skincare</td>
      <td>SKU4</td>
      <td>4.805496</td>
      <td>26</td>
      <td>871</td>
      <td>2686.505152</td>
      <td>Non-binary</td>
      <td>5</td>
      <td>3</td>
      <td>56</td>
      <td>...</td>
      <td>Delhi</td>
      <td>5</td>
      <td>414</td>
      <td>3</td>
      <td>92.065161</td>
      <td>Fail</td>
      <td>3.145580</td>
      <td>Air</td>
      <td>Route A</td>
      <td>923.440632</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 24 columns</p>
</div>




```python
df.tail()
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
      <th>Product type</th>
      <th>SKU</th>
      <th>Price</th>
      <th>Availability</th>
      <th>Number of products sold</th>
      <th>Revenue generated</th>
      <th>Customer demographics</th>
      <th>Stock levels</th>
      <th>Lead times</th>
      <th>Order quantities</th>
      <th>...</th>
      <th>Location</th>
      <th>Lead time</th>
      <th>Production volumes</th>
      <th>Manufacturing lead time</th>
      <th>Manufacturing costs</th>
      <th>Inspection results</th>
      <th>Defect rates</th>
      <th>Transportation modes</th>
      <th>Routes</th>
      <th>Costs</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>95</th>
      <td>haircare</td>
      <td>SKU95</td>
      <td>77.903927</td>
      <td>65</td>
      <td>672</td>
      <td>7386.363944</td>
      <td>Unknown</td>
      <td>15</td>
      <td>14</td>
      <td>26</td>
      <td>...</td>
      <td>Mumbai</td>
      <td>18</td>
      <td>450</td>
      <td>26</td>
      <td>58.890686</td>
      <td>Pending</td>
      <td>1.210882</td>
      <td>Air</td>
      <td>Route A</td>
      <td>778.864241</td>
    </tr>
    <tr>
      <th>96</th>
      <td>cosmetics</td>
      <td>SKU96</td>
      <td>24.423131</td>
      <td>29</td>
      <td>324</td>
      <td>7698.424766</td>
      <td>Non-binary</td>
      <td>67</td>
      <td>2</td>
      <td>32</td>
      <td>...</td>
      <td>Mumbai</td>
      <td>28</td>
      <td>648</td>
      <td>28</td>
      <td>17.803756</td>
      <td>Pending</td>
      <td>3.872048</td>
      <td>Road</td>
      <td>Route A</td>
      <td>188.742141</td>
    </tr>
    <tr>
      <th>97</th>
      <td>haircare</td>
      <td>SKU97</td>
      <td>3.526111</td>
      <td>56</td>
      <td>62</td>
      <td>4370.916580</td>
      <td>Male</td>
      <td>46</td>
      <td>19</td>
      <td>4</td>
      <td>...</td>
      <td>Mumbai</td>
      <td>10</td>
      <td>535</td>
      <td>13</td>
      <td>65.765156</td>
      <td>Fail</td>
      <td>3.376238</td>
      <td>Road</td>
      <td>Route A</td>
      <td>540.132423</td>
    </tr>
    <tr>
      <th>98</th>
      <td>skincare</td>
      <td>SKU98</td>
      <td>19.754605</td>
      <td>43</td>
      <td>913</td>
      <td>8525.952560</td>
      <td>Female</td>
      <td>53</td>
      <td>1</td>
      <td>27</td>
      <td>...</td>
      <td>Chennai</td>
      <td>28</td>
      <td>581</td>
      <td>9</td>
      <td>5.604691</td>
      <td>Pending</td>
      <td>2.908122</td>
      <td>Rail</td>
      <td>Route A</td>
      <td>882.198864</td>
    </tr>
    <tr>
      <th>99</th>
      <td>haircare</td>
      <td>SKU99</td>
      <td>68.517833</td>
      <td>17</td>
      <td>627</td>
      <td>9185.185829</td>
      <td>Unknown</td>
      <td>55</td>
      <td>8</td>
      <td>59</td>
      <td>...</td>
      <td>Chennai</td>
      <td>29</td>
      <td>921</td>
      <td>2</td>
      <td>38.072899</td>
      <td>Fail</td>
      <td>0.346027</td>
      <td>Rail</td>
      <td>Route B</td>
      <td>210.743009</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 24 columns</p>
</div>




```python
df.shape
```




    (100, 24)




```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 100 entries, 0 to 99
    Data columns (total 24 columns):
     #   Column                   Non-Null Count  Dtype  
    ---  ------                   --------------  -----  
     0   Product type             100 non-null    object 
     1   SKU                      100 non-null    object 
     2   Price                    100 non-null    float64
     3   Availability             100 non-null    int64  
     4   Number of products sold  100 non-null    int64  
     5   Revenue generated        100 non-null    float64
     6   Customer demographics    100 non-null    object 
     7   Stock levels             100 non-null    int64  
     8   Lead times               100 non-null    int64  
     9   Order quantities         100 non-null    int64  
     10  Shipping times           100 non-null    int64  
     11  Shipping carriers        100 non-null    object 
     12  Shipping costs           100 non-null    float64
     13  Supplier name            100 non-null    object 
     14  Location                 100 non-null    object 
     15  Lead time                100 non-null    int64  
     16  Production volumes       100 non-null    int64  
     17  Manufacturing lead time  100 non-null    int64  
     18  Manufacturing costs      100 non-null    float64
     19  Inspection results       100 non-null    object 
     20  Defect rates             100 non-null    float64
     21  Transportation modes     100 non-null    object 
     22  Routes                   100 non-null    object 
     23  Costs                    100 non-null    float64
    dtypes: float64(6), int64(9), object(9)
    memory usage: 18.9+ KB
    


```python
df.describe()
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
      <th>Price</th>
      <th>Availability</th>
      <th>Number of products sold</th>
      <th>Revenue generated</th>
      <th>Stock levels</th>
      <th>Lead times</th>
      <th>Order quantities</th>
      <th>Shipping times</th>
      <th>Shipping costs</th>
      <th>Lead time</th>
      <th>Production volumes</th>
      <th>Manufacturing lead time</th>
      <th>Manufacturing costs</th>
      <th>Defect rates</th>
      <th>Costs</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>100.000000</td>
      <td>100.000000</td>
      <td>100.000000</td>
      <td>100.000000</td>
      <td>100.000000</td>
      <td>100.000000</td>
      <td>100.000000</td>
      <td>100.000000</td>
      <td>100.000000</td>
      <td>100.000000</td>
      <td>100.000000</td>
      <td>100.00000</td>
      <td>100.000000</td>
      <td>100.000000</td>
      <td>100.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>49.462461</td>
      <td>48.400000</td>
      <td>460.990000</td>
      <td>5776.048187</td>
      <td>47.770000</td>
      <td>15.960000</td>
      <td>49.220000</td>
      <td>5.750000</td>
      <td>5.548149</td>
      <td>17.080000</td>
      <td>567.840000</td>
      <td>14.77000</td>
      <td>47.266693</td>
      <td>2.277158</td>
      <td>529.245782</td>
    </tr>
    <tr>
      <th>std</th>
      <td>31.168193</td>
      <td>30.743317</td>
      <td>303.780074</td>
      <td>2732.841744</td>
      <td>31.369372</td>
      <td>8.785801</td>
      <td>26.784429</td>
      <td>2.724283</td>
      <td>2.651376</td>
      <td>8.846251</td>
      <td>263.046861</td>
      <td>8.91243</td>
      <td>28.982841</td>
      <td>1.461366</td>
      <td>258.301696</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.699976</td>
      <td>1.000000</td>
      <td>8.000000</td>
      <td>1061.618523</td>
      <td>0.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.013487</td>
      <td>1.000000</td>
      <td>104.000000</td>
      <td>1.00000</td>
      <td>1.085069</td>
      <td>0.018608</td>
      <td>103.916248</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>19.597823</td>
      <td>22.750000</td>
      <td>184.250000</td>
      <td>2812.847151</td>
      <td>16.750000</td>
      <td>8.000000</td>
      <td>26.000000</td>
      <td>3.750000</td>
      <td>3.540248</td>
      <td>10.000000</td>
      <td>352.000000</td>
      <td>7.00000</td>
      <td>22.983299</td>
      <td>1.009650</td>
      <td>318.778455</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>51.239831</td>
      <td>43.500000</td>
      <td>392.500000</td>
      <td>6006.352023</td>
      <td>47.500000</td>
      <td>17.000000</td>
      <td>52.000000</td>
      <td>6.000000</td>
      <td>5.320534</td>
      <td>18.000000</td>
      <td>568.500000</td>
      <td>14.00000</td>
      <td>45.905622</td>
      <td>2.141863</td>
      <td>520.430444</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>77.198228</td>
      <td>75.000000</td>
      <td>704.250000</td>
      <td>8253.976921</td>
      <td>73.000000</td>
      <td>24.000000</td>
      <td>71.250000</td>
      <td>8.000000</td>
      <td>7.601695</td>
      <td>25.000000</td>
      <td>797.000000</td>
      <td>23.00000</td>
      <td>68.621026</td>
      <td>3.563995</td>
      <td>763.078231</td>
    </tr>
    <tr>
      <th>max</th>
      <td>99.171329</td>
      <td>100.000000</td>
      <td>996.000000</td>
      <td>9866.465458</td>
      <td>100.000000</td>
      <td>30.000000</td>
      <td>96.000000</td>
      <td>10.000000</td>
      <td>9.929816</td>
      <td>30.000000</td>
      <td>985.000000</td>
      <td>30.00000</td>
      <td>99.466109</td>
      <td>4.939255</td>
      <td>997.413450</td>
    </tr>
  </tbody>
</table>
</div>



## Data Cleaning


```python
# Checking for duplicate rows
duplicates = df.duplicated()
print(f'Duplicate rows = {duplicates.sum()}')
```

    Duplicate rows = 0
    


```python
# Checking for missing data
df.isnull().sum()

```




    Product type               0
    SKU                        0
    Price                      0
    Availability               0
    Number of products sold    0
    Revenue generated          0
    Customer demographics      0
    Stock levels               0
    Lead times                 0
    Order quantities           0
    Shipping times             0
    Shipping carriers          0
    Shipping costs             0
    Supplier name              0
    Location                   0
    Lead time                  0
    Production volumes         0
    Manufacturing lead time    0
    Manufacturing costs        0
    Inspection results         0
    Defect rates               0
    Transportation modes       0
    Routes                     0
    Costs                      0
    dtype: int64



I will check for outliers using the Z-score method, values that are more than 3 standard deviations away from the mean will be considered outliers.


```python
# CheckING for outliers using the Z-score method
z_scores = (df - df.mean()) / df.std()
outliers = (z_scores > 3) | (z_scores < -3)
print(f'Outliers:\n{outliers}')
```

    Outliers:
        Availability  Costs  Customer demographics  Defect rates  \
    0          False  False                  False         False   
    1          False  False                  False         False   
    2          False  False                  False         False   
    3          False  False                  False         False   
    4          False  False                  False         False   
    ..           ...    ...                    ...           ...   
    95         False  False                  False         False   
    96         False  False                  False         False   
    97         False  False                  False         False   
    98         False  False                  False         False   
    99         False  False                  False         False   
    
        Inspection results  Lead time  Lead times  Location  Manufacturing costs  \
    0                False      False       False     False                False   
    1                False      False       False     False                False   
    2                False      False       False     False                False   
    3                False      False       False     False                False   
    4                False      False       False     False                False   
    ..                 ...        ...         ...       ...                  ...   
    95               False      False       False     False                False   
    96               False      False       False     False                False   
    97               False      False       False     False                False   
    98               False      False       False     False                False   
    99               False      False       False     False                False   
    
        Manufacturing lead time  ...  Production volumes  Revenue generated  \
    0                     False  ...               False              False   
    1                     False  ...               False              False   
    2                     False  ...               False              False   
    3                     False  ...               False              False   
    4                     False  ...               False              False   
    ..                      ...  ...                 ...                ...   
    95                    False  ...               False              False   
    96                    False  ...               False              False   
    97                    False  ...               False              False   
    98                    False  ...               False              False   
    99                    False  ...               False              False   
    
        Routes    SKU  Shipping carriers  Shipping costs  Shipping times  \
    0    False  False              False           False           False   
    1    False  False              False           False           False   
    2    False  False              False           False           False   
    3    False  False              False           False           False   
    4    False  False              False           False           False   
    ..     ...    ...                ...             ...             ...   
    95   False  False              False           False           False   
    96   False  False              False           False           False   
    97   False  False              False           False           False   
    98   False  False              False           False           False   
    99   False  False              False           False           False   
    
        Stock levels  Supplier name  Transportation modes  
    0          False          False                 False  
    1          False          False                 False  
    2          False          False                 False  
    3          False          False                 False  
    4          False          False                 False  
    ..           ...            ...                   ...  
    95         False          False                 False  
    96         False          False                 False  
    97         False          False                 False  
    98         False          False                 False  
    99         False          False                 False  
    
    [100 rows x 24 columns]
    


```python
# Calculating the IQR for each column
Q1 = df.quantile(0.25)
Q3 = df.quantile(0.75)
IQR = Q3 - Q1

# Finding the outliers
outliers = (df < (Q1 - 1.5 * IQR)) | (df > (Q3 + 1.5 * IQR))
outliers
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
      <th>Availability</th>
      <th>Costs</th>
      <th>Customer demographics</th>
      <th>Defect rates</th>
      <th>Inspection results</th>
      <th>Lead time</th>
      <th>Lead times</th>
      <th>Location</th>
      <th>Manufacturing costs</th>
      <th>Manufacturing lead time</th>
      <th>...</th>
      <th>Production volumes</th>
      <th>Revenue generated</th>
      <th>Routes</th>
      <th>SKU</th>
      <th>Shipping carriers</th>
      <th>Shipping costs</th>
      <th>Shipping times</th>
      <th>Stock levels</th>
      <th>Supplier name</th>
      <th>Transportation modes</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>4</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
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
      <th>95</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>96</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>97</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>98</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>99</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
<p>100 rows × 24 columns</p>
</div>



## Data Exploration

### Correlation Matrix



```python
corr_matrix =df.corr()
corr_matrix
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
      <th>Price</th>
      <th>Availability</th>
      <th>Number of products sold</th>
      <th>Revenue generated</th>
      <th>Stock levels</th>
      <th>Lead times</th>
      <th>Order quantities</th>
      <th>Shipping times</th>
      <th>Shipping costs</th>
      <th>Lead time</th>
      <th>Production volumes</th>
      <th>Manufacturing lead time</th>
      <th>Manufacturing costs</th>
      <th>Defect rates</th>
      <th>Costs</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Price</th>
      <td>1.000000</td>
      <td>0.019083</td>
      <td>0.005739</td>
      <td>0.038424</td>
      <td>0.078261</td>
      <td>0.044855</td>
      <td>0.095819</td>
      <td>0.071942</td>
      <td>0.058543</td>
      <td>0.152185</td>
      <td>-0.124575</td>
      <td>-0.301313</td>
      <td>-0.184123</td>
      <td>-0.147247</td>
      <td>0.088501</td>
    </tr>
    <tr>
      <th>Availability</th>
      <td>0.019083</td>
      <td>1.000000</td>
      <td>0.087496</td>
      <td>-0.075170</td>
      <td>-0.025900</td>
      <td>0.170439</td>
      <td>0.143769</td>
      <td>-0.051377</td>
      <td>-0.044179</td>
      <td>-0.156669</td>
      <td>0.050134</td>
      <td>0.065333</td>
      <td>0.134652</td>
      <td>0.040626</td>
      <td>-0.027315</td>
    </tr>
    <tr>
      <th>Number of products sold</th>
      <td>0.005739</td>
      <td>0.087496</td>
      <td>1.000000</td>
      <td>-0.001641</td>
      <td>0.022189</td>
      <td>-0.046419</td>
      <td>0.015992</td>
      <td>0.087315</td>
      <td>0.044285</td>
      <td>0.041230</td>
      <td>0.187945</td>
      <td>-0.048939</td>
      <td>0.034284</td>
      <td>-0.082726</td>
      <td>-0.036951</td>
    </tr>
    <tr>
      <th>Revenue generated</th>
      <td>0.038424</td>
      <td>-0.075170</td>
      <td>-0.001641</td>
      <td>1.000000</td>
      <td>-0.158480</td>
      <td>-0.057296</td>
      <td>0.029422</td>
      <td>-0.109211</td>
      <td>-0.072892</td>
      <td>-0.014178</td>
      <td>-0.037441</td>
      <td>0.014073</td>
      <td>-0.214025</td>
      <td>-0.125335</td>
      <td>0.027252</td>
    </tr>
    <tr>
      <th>Stock levels</th>
      <td>0.078261</td>
      <td>-0.025900</td>
      <td>0.022189</td>
      <td>-0.158480</td>
      <td>1.000000</td>
      <td>0.072571</td>
      <td>-0.111455</td>
      <td>-0.094883</td>
      <td>0.072907</td>
      <td>0.067880</td>
      <td>0.043763</td>
      <td>-0.050592</td>
      <td>0.033243</td>
      <td>-0.149478</td>
      <td>-0.012088</td>
    </tr>
    <tr>
      <th>Lead times</th>
      <td>0.044855</td>
      <td>0.170439</td>
      <td>-0.046419</td>
      <td>-0.057296</td>
      <td>0.072571</td>
      <td>1.000000</td>
      <td>0.105459</td>
      <td>-0.045156</td>
      <td>-0.120746</td>
      <td>-0.002818</td>
      <td>-0.145324</td>
      <td>0.003364</td>
      <td>-0.024441</td>
      <td>0.015681</td>
      <td>0.243686</td>
    </tr>
    <tr>
      <th>Order quantities</th>
      <td>0.095819</td>
      <td>0.143769</td>
      <td>0.015992</td>
      <td>0.029422</td>
      <td>-0.111455</td>
      <td>0.105459</td>
      <td>1.000000</td>
      <td>-0.002561</td>
      <td>0.004261</td>
      <td>-0.086189</td>
      <td>-0.086567</td>
      <td>0.112347</td>
      <td>-0.026784</td>
      <td>0.018986</td>
      <td>0.167306</td>
    </tr>
    <tr>
      <th>Shipping times</th>
      <td>0.071942</td>
      <td>-0.051377</td>
      <td>0.087315</td>
      <td>-0.109211</td>
      <td>-0.094883</td>
      <td>-0.045156</td>
      <td>-0.002561</td>
      <td>1.000000</td>
      <td>0.045108</td>
      <td>-0.022214</td>
      <td>-0.060470</td>
      <td>-0.016953</td>
      <td>0.029132</td>
      <td>-0.036673</td>
      <td>-0.045541</td>
    </tr>
    <tr>
      <th>Shipping costs</th>
      <td>0.058543</td>
      <td>-0.044179</td>
      <td>0.044285</td>
      <td>-0.072892</td>
      <td>0.072907</td>
      <td>-0.120746</td>
      <td>0.004261</td>
      <td>0.045108</td>
      <td>1.000000</td>
      <td>0.029680</td>
      <td>-0.097979</td>
      <td>-0.005653</td>
      <td>0.005984</td>
      <td>0.083139</td>
      <td>0.051671</td>
    </tr>
    <tr>
      <th>Lead time</th>
      <td>0.152185</td>
      <td>-0.156669</td>
      <td>0.041230</td>
      <td>-0.014178</td>
      <td>0.067880</td>
      <td>-0.002818</td>
      <td>-0.086189</td>
      <td>-0.022214</td>
      <td>0.029680</td>
      <td>1.000000</td>
      <td>0.212676</td>
      <td>0.026756</td>
      <td>-0.121999</td>
      <td>0.297099</td>
      <td>0.045219</td>
    </tr>
    <tr>
      <th>Production volumes</th>
      <td>-0.124575</td>
      <td>0.050134</td>
      <td>0.187945</td>
      <td>-0.037441</td>
      <td>0.043763</td>
      <td>-0.145324</td>
      <td>-0.086567</td>
      <td>-0.060470</td>
      <td>-0.097979</td>
      <td>0.212676</td>
      <td>1.000000</td>
      <td>0.184457</td>
      <td>0.051504</td>
      <td>0.118853</td>
      <td>-0.074927</td>
    </tr>
    <tr>
      <th>Manufacturing lead time</th>
      <td>-0.301313</td>
      <td>0.065333</td>
      <td>-0.048939</td>
      <td>0.014073</td>
      <td>-0.050592</td>
      <td>0.003364</td>
      <td>0.112347</td>
      <td>-0.016953</td>
      <td>-0.005653</td>
      <td>0.026756</td>
      <td>0.184457</td>
      <td>1.000000</td>
      <td>-0.158098</td>
      <td>0.139518</td>
      <td>-0.074092</td>
    </tr>
    <tr>
      <th>Manufacturing costs</th>
      <td>-0.184123</td>
      <td>0.134652</td>
      <td>0.034284</td>
      <td>-0.214025</td>
      <td>0.033243</td>
      <td>-0.024441</td>
      <td>-0.026784</td>
      <td>0.029132</td>
      <td>0.005984</td>
      <td>-0.121999</td>
      <td>0.051504</td>
      <td>-0.158098</td>
      <td>1.000000</td>
      <td>-0.007819</td>
      <td>-0.013911</td>
    </tr>
    <tr>
      <th>Defect rates</th>
      <td>-0.147247</td>
      <td>0.040626</td>
      <td>-0.082726</td>
      <td>-0.125335</td>
      <td>-0.149478</td>
      <td>0.015681</td>
      <td>0.018986</td>
      <td>-0.036673</td>
      <td>0.083139</td>
      <td>0.297099</td>
      <td>0.118853</td>
      <td>0.139518</td>
      <td>-0.007819</td>
      <td>1.000000</td>
      <td>0.032072</td>
    </tr>
    <tr>
      <th>Costs</th>
      <td>0.088501</td>
      <td>-0.027315</td>
      <td>-0.036951</td>
      <td>0.027252</td>
      <td>-0.012088</td>
      <td>0.243686</td>
      <td>0.167306</td>
      <td>-0.045541</td>
      <td>0.051671</td>
      <td>0.045219</td>
      <td>-0.074927</td>
      <td>-0.074092</td>
      <td>-0.013911</td>
      <td>0.032072</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Visualizing the matrix
plt.figure(figsize=(10, 8))
sns.heatmap(corr_matrix, annot=True, cmap='coolwarm')
plt.show()
```


    
![png](Supply-Chain-Analysis_files/Supply-Chain-Analysis_15_0.png)
    


Observations:
- There is a strong negative correlation between Price and Manufacturing lead time (-0.301), indicating that as the price of a product increases, the manufacturing lead time tends to decrease.
- There is also a strong negative correlation between Revenue generated and Manufacturing costs (-0.214), indicating that as the revenue generated by a product increases, the manufacturing costs tend to decrease.
- Lead time has a strong positive correlation with Defect rates (0.297), indicating that as the lead time for a product increases, the defect rates also tend to increase.
- There is a moderate positive correlation between Lead times and Costs (0.243), indicating that as the lead time for a product increases, the costs also tend to increase.
- There is a moderate negative correlation between Price and Production volumes (-0.124), indicating that as the price of a product increases, the production volumes tend to decrease.

#### 1. Product type and SKU

This will provide information about which products are most popular and profitable.


```python
# Calculating the number of products sold by product type and SKU
top_20_skus = df.groupby('SKU')['Number of products sold'].sum().sort_values(ascending=False).head(20)
top_20_skus = top_20_skus.reset_index()
top_20_skus
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
      <th>SKU</th>
      <th>Number of products sold</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>SKU10</td>
      <td>996</td>
    </tr>
    <tr>
      <th>1</th>
      <td>SKU94</td>
      <td>987</td>
    </tr>
    <tr>
      <th>2</th>
      <td>SKU9</td>
      <td>980</td>
    </tr>
    <tr>
      <th>3</th>
      <td>SKU37</td>
      <td>963</td>
    </tr>
    <tr>
      <th>4</th>
      <td>SKU36</td>
      <td>963</td>
    </tr>
    <tr>
      <th>5</th>
      <td>SKU11</td>
      <td>960</td>
    </tr>
    <tr>
      <th>6</th>
      <td>SKU78</td>
      <td>946</td>
    </tr>
    <tr>
      <th>7</th>
      <td>SKU40</td>
      <td>933</td>
    </tr>
    <tr>
      <th>8</th>
      <td>SKU44</td>
      <td>919</td>
    </tr>
    <tr>
      <th>9</th>
      <td>SKU91</td>
      <td>916</td>
    </tr>
    <tr>
      <th>10</th>
      <td>SKU98</td>
      <td>913</td>
    </tr>
    <tr>
      <th>11</th>
      <td>SKU47</td>
      <td>910</td>
    </tr>
    <tr>
      <th>12</th>
      <td>SKU74</td>
      <td>904</td>
    </tr>
    <tr>
      <th>13</th>
      <td>SKU58</td>
      <td>896</td>
    </tr>
    <tr>
      <th>14</th>
      <td>SKU22</td>
      <td>884</td>
    </tr>
    <tr>
      <th>15</th>
      <td>SKU80</td>
      <td>872</td>
    </tr>
    <tr>
      <th>16</th>
      <td>SKU4</td>
      <td>871</td>
    </tr>
    <tr>
      <th>17</th>
      <td>SKU46</td>
      <td>859</td>
    </tr>
    <tr>
      <th>18</th>
      <td>SKU52</td>
      <td>820</td>
    </tr>
    <tr>
      <th>19</th>
      <td>SKU0</td>
      <td>802</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Creating a bar plot
fig, ax = plt.subplots()
top_20_skus.plot.bar(x='SKU', y='Number of products sold', ax=ax)
ax.set_title('Top 20 SKUs by Number of Products Sold')
ax.set_xlabel('SKU')
ax.set_ylabel('Number of Products Sold')
plt.show()
```


    
![png](Supply-Chain-Analysis_files/Supply-Chain-Analysis_20_0.png)
    


#### 2. Price and availability

This will provide information on how pricing and inventory management strategies impact sales and revenue.


```python
# Calculating the average price and availability by product type
price_availability = df.groupby('Product type')[['Price', 'Availability']].mean()
price_availability = price_availability.reset_index()
price_availability
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
      <th>Product type</th>
      <th>Price</th>
      <th>Availability</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>cosmetics</td>
      <td>57.361058</td>
      <td>51.230769</td>
    </tr>
    <tr>
      <th>1</th>
      <td>haircare</td>
      <td>46.014279</td>
      <td>43.264706</td>
    </tr>
    <tr>
      <th>2</th>
      <td>skincare</td>
      <td>47.259329</td>
      <td>50.925000</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Creating a bar plot
fig, ax = plt.subplots()
price_availability.plot.bar(x='Product type', y=['Price', 'Availability'], ax=ax)
ax.set_title('Average Price and Availability by Product Type')
ax.set_xlabel('Product Type')
ax.set_ylabel('Price and Availability')
plt.show()
```


    
![png](Supply-Chain-Analysis_files/Supply-Chain-Analysis_24_0.png)
    


#### 3. Number of products sold and revenue generated

This will provide information about sales performance and can help understand which products are driving revenue and growth.


```python
# Calculating the total number of products sold and revenue generated by product type
sales_revenue = df.groupby('Product type')[['Number of products sold', 'Revenue generated']].sum()
sales_revenue = sales_revenue.reset_index()
sales_revenue
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
      <th>Product type</th>
      <th>Number of products sold</th>
      <th>Revenue generated</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>cosmetics</td>
      <td>11757</td>
      <td>161521.265999</td>
    </tr>
    <tr>
      <th>1</th>
      <td>haircare</td>
      <td>13611</td>
      <td>174455.390605</td>
    </tr>
    <tr>
      <th>2</th>
      <td>skincare</td>
      <td>20731</td>
      <td>241628.162133</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Creating a bar plot
fig, ax = plt.subplots()
sales_revenue.plot.bar(x='Product type', y=['Number of products sold', 'Revenue generated'], ax=ax)
ax.set_title('Total Number of Products Sold and Revenue Generated by Product Type')
ax.set_xlabel('Product Type')
ax.set_ylabel('Number of Products Sold and Revenue Generated')
plt.show()
```


    
![png](Supply-Chain-Analysis_files/Supply-Chain-Analysis_28_0.png)
    


#### 4. Customer demographics

This will provide more information about the characteristics of customers hence help understand their needs and preferences.


```python
# Calculating the number of products sold by customer demographics
customer_sales = df.groupby(['Customer demographics', 'Product type'])['Number of products sold'].sum()
customer_sales = customer_sales.reset_index()
customer_sales
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
      <th>Customer demographics</th>
      <th>Product type</th>
      <th>Number of products sold</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Female</td>
      <td>cosmetics</td>
      <td>4012</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Female</td>
      <td>haircare</td>
      <td>936</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Female</td>
      <td>skincare</td>
      <td>7853</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Male</td>
      <td>cosmetics</td>
      <td>2304</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Male</td>
      <td>haircare</td>
      <td>2292</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Male</td>
      <td>skincare</td>
      <td>2911</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Non-binary</td>
      <td>cosmetics</td>
      <td>2607</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Non-binary</td>
      <td>haircare</td>
      <td>2820</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Non-binary</td>
      <td>skincare</td>
      <td>5153</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Unknown</td>
      <td>cosmetics</td>
      <td>2834</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Unknown</td>
      <td>haircare</td>
      <td>7563</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Unknown</td>
      <td>skincare</td>
      <td>4814</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Creating a bar plot
fig, ax = plt.subplots()
customer_sales.plot.bar(x='Customer demographics', y='Number of products sold', ax=ax)
ax.set_title('Number of Products Sold by Customer Demographics')
ax.set_xlabel('Customer Demographics')
ax.set_ylabel('Number of Products Sold')
plt.show()
```


    
![png](Supply-Chain-Analysis_files/Supply-Chain-Analysis_32_0.png)
    


#### 5. Stock levels, lead times, and order quantities

This will more provide information about inventory management and can help optimize the Supply Chain to ensure that products are available when customers want them. 


```python
# Calculating the average stock levels, lead times, and order quantities by product type
inventory_metrics = df.groupby('Product type')[['Stock levels', 'Lead times', 'Order quantities']].mean()
inventory_metrics = inventory_metrics.reset_index()
inventory_metrics
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
      <th>Product type</th>
      <th>Stock levels</th>
      <th>Lead times</th>
      <th>Order quantities</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>cosmetics</td>
      <td>58.653846</td>
      <td>15.384615</td>
      <td>51.653846</td>
    </tr>
    <tr>
      <th>1</th>
      <td>haircare</td>
      <td>48.352941</td>
      <td>15.529412</td>
      <td>43.529412</td>
    </tr>
    <tr>
      <th>2</th>
      <td>skincare</td>
      <td>40.200000</td>
      <td>16.700000</td>
      <td>52.475000</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Creating a bar plot
fig, ax = plt.subplots()
inventory_metrics.plot.bar(x='Product type', y=['Stock levels', 'Lead times', 'Order quantities'], ax=ax)
ax.set_title('Average Stock Levels, Lead Times, and Order Quantities by Product Type')
ax.set_xlabel('Product Type')
ax.set_ylabel('Stock Levels, Lead Times, and Order Quantities')
plt.show()
```


    
![png](Supply-Chain-Analysis_files/Supply-Chain-Analysis_36_0.png)
    


#### 6. Location, Production volumes, Manufacturing lead time, Manufacturing costs

These will provide more information about the production process and can help identify opportunities to improve efficiency and reduce costs.


```python
# Calculate the average production volumes, manufacturing lead time, and manufacturing costs by location
production_metrics = df.groupby('Location')[['Production volumes', 'Manufacturing lead time', 'Manufacturing costs']].mean()
production_metrics = production_metrics.reset_index()
production_metrics
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
      <th>Location</th>
      <th>Production volumes</th>
      <th>Manufacturing lead time</th>
      <th>Manufacturing costs</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Bangalore</td>
      <td>434.833333</td>
      <td>11.777778</td>
      <td>61.994977</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Chennai</td>
      <td>599.200000</td>
      <td>12.650000</td>
      <td>51.145043</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Delhi</td>
      <td>557.466667</td>
      <td>13.533333</td>
      <td>48.880026</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Kolkata</td>
      <td>618.040000</td>
      <td>15.000000</td>
      <td>41.863122</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Mumbai</td>
      <td>598.181818</td>
      <td>19.727273</td>
      <td>36.730928</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Create a bar plot
fig, ax = plt.subplots()
production_metrics.plot.bar(x='Location', y=['Production volumes', 'Manufacturing lead time', 'Manufacturing costs'], ax=ax)
ax.set_title('Average Production Volumes, Manufacturing Lead Time, and Manufacturing Costs by Location')
ax.set_xlabel('Location')
ax.set_ylabel('Production Volumes, Manufacturing Lead Time, and Manufacturing Costs')
plt.show()
```


    
![png](Supply-Chain-Analysis_files/Supply-Chain-Analysis_40_0.png)
    


#### 7. Shipping Costs


```python
shipping= df.groupby('Shipping carriers')['Shipping costs'].sum()
shipping = shipping.reset_index()
shipping 
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
      <th>Shipping carriers</th>
      <th>Shipping costs</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Carrier A</td>
      <td>155.537831</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Carrier B</td>
      <td>236.897620</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Carrier C</td>
      <td>162.379457</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Creating a bar plot
fig, ax = plt.subplots()
shipping.plot.bar(x='Shipping carriers', y='Shipping costs', ax=ax)
ax.set_title('Total Shipping Costs by Shipping Carrier')
ax.set_xlabel('Shipping Carrier')
ax.set_ylabel('Shipping Costs')
plt.show()
```


    
![png](Supply-Chain-Analysis_files/Supply-Chain-Analysis_43_0.png)
    



```python

```
