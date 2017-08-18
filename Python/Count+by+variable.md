
## Import modules


```python
import pandas as pd
```

## Create dataframe
We'll use pothole data located [here](http://data.syrgov.net/datasets/potholes-filled)


```python
potholes_filled = pd.read_csv('potholes_filled.csv')
```

## Count by variable


```python
potholes_filled.groupby(['TNT_NAME']).size()
```




    TNT_NAME
    Downtown      911
    Eastside     3056
    Eastwood      620
    Lakefront     476
    Northside    1171
    Southside     552
    Valley        184
    Westside      438
    dtype: int64




```python

```
