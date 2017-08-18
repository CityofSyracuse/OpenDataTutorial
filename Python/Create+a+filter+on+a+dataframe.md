
##Import modules


```python
import pandas as pd
```

##Create dataframe
We'll use pothole data located [here](http://data.syrgov.net/datasets/potholes-filled)


```python
potholes_filled = pd.read_csv("potholes_filled.csv")
potholes_filled.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>X</th>
      <th>Y</th>
      <th>truck_name</th>
      <th>repair_type</th>
      <th>date_fixed</th>
      <th>address</th>
      <th>activity_type</th>
      <th>longitude</th>
      <th>latitude</th>
      <th>TNT_NAME</th>
      <th>FID</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>-76.079956</td>
      <td>43.039362</td>
      <td>DP2</td>
      <td>STREET REPAIR</td>
      <td>2017-08-08T10:42:24.000Z</td>
      <td>100 STONERIDGE DR &amp; GENESEE S                 ...</td>
      <td>Accessory On</td>
      <td>-76.079956</td>
      <td>43.039362</td>
      <td>Eastside</td>
      <td>7001</td>
    </tr>
    <tr>
      <th>1</th>
      <td>-76.079947</td>
      <td>43.039452</td>
      <td>DP2</td>
      <td>STREET REPAIR</td>
      <td>2017-08-08T10:47:12.000Z</td>
      <td>101 STONERIDGE DR &amp; GENESEE S                 ...</td>
      <td>Accessory On</td>
      <td>-76.079947</td>
      <td>43.039452</td>
      <td>Eastside</td>
      <td>7002</td>
    </tr>
    <tr>
      <th>2</th>
      <td>-76.079875</td>
      <td>43.039476</td>
      <td>DP2</td>
      <td>STREET REPAIR</td>
      <td>2017-08-08T10:53:56.000Z</td>
      <td>101 STONERIDGE DR &amp; GENESEE S                 ...</td>
      <td>Accessory On</td>
      <td>-76.079875</td>
      <td>43.039476</td>
      <td>Eastside</td>
      <td>7003</td>
    </tr>
    <tr>
      <th>3</th>
      <td>-76.079784</td>
      <td>43.039547</td>
      <td>DP2</td>
      <td>STREET REPAIR</td>
      <td>2017-08-08T10:58:03.000Z</td>
      <td>102 STONERIDGE DR                             ...</td>
      <td>Accessory On</td>
      <td>-76.079784</td>
      <td>43.039547</td>
      <td>Eastside</td>
      <td>7004</td>
    </tr>
    <tr>
      <th>4</th>
      <td>-76.130881</td>
      <td>42.999335</td>
      <td>DP2</td>
      <td>STREET REPAIR</td>
      <td>2017-08-11T06:47:12.000Z</td>
      <td>154 LAFAYETTE RD                              ...</td>
      <td>Accessory On</td>
      <td>-76.130881</td>
      <td>42.999335</td>
      <td>Valley</td>
      <td>7005</td>
    </tr>
  </tbody>
</table>
</div>



##Filter dataframe to only see potholes filled in the Valley


```python
valley_potholes = potholes_filled[potholes_filled['TNT_NAME'] == 'Valley']
valley_potholes.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>X</th>
      <th>Y</th>
      <th>truck_name</th>
      <th>repair_type</th>
      <th>date_fixed</th>
      <th>address</th>
      <th>activity_type</th>
      <th>longitude</th>
      <th>latitude</th>
      <th>TNT_NAME</th>
      <th>FID</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>4</th>
      <td>-76.130881</td>
      <td>42.999335</td>
      <td>DP2</td>
      <td>STREET REPAIR</td>
      <td>2017-08-11T06:47:12.000Z</td>
      <td>154 LAFAYETTE RD                              ...</td>
      <td>Accessory On</td>
      <td>-76.130881</td>
      <td>42.999335</td>
      <td>Valley</td>
      <td>7005</td>
    </tr>
    <tr>
      <th>6</th>
      <td>-76.129814</td>
      <td>42.999723</td>
      <td>DP2</td>
      <td>STREET REPAIR</td>
      <td>2017-08-11T06:48:09.000Z</td>
      <td>139 LAFAYETTE RD SYRACUSE 13205               ...</td>
      <td>Accessory On</td>
      <td>-76.129814</td>
      <td>42.999723</td>
      <td>Valley</td>
      <td>7007</td>
    </tr>
    <tr>
      <th>8</th>
      <td>-76.130788</td>
      <td>42.999313</td>
      <td>DP2</td>
      <td>STREET REPAIR</td>
      <td>2017-08-11T06:49:50.000Z</td>
      <td>154 LAFAYETTE RD                              ...</td>
      <td>Accessory On</td>
      <td>-76.130788</td>
      <td>42.999313</td>
      <td>Valley</td>
      <td>7009</td>
    </tr>
    <tr>
      <th>10</th>
      <td>-76.130968</td>
      <td>42.999302</td>
      <td>DP2</td>
      <td>STREET REPAIR</td>
      <td>2017-08-11T06:50:45.000Z</td>
      <td>154 LAFAYETTE RD                              ...</td>
      <td>Accessory On</td>
      <td>-76.130968</td>
      <td>42.999302</td>
      <td>Valley</td>
      <td>7011</td>
    </tr>
    <tr>
      <th>414</th>
      <td>-76.131176</td>
      <td>42.997632</td>
      <td>DP2</td>
      <td>STREET REPAIR</td>
      <td>2017-08-11T06:28:18.000Z</td>
      <td>212 LAFAYETTE RD SYRACUSE 13205               ...</td>
      <td>Accessory On</td>
      <td>-76.131176</td>
      <td>42.997632</td>
      <td>Valley</td>
      <td>7415</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
