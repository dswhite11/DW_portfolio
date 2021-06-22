```python
%pip install seaborn
```

    Defaulting to user installation because normal site-packages is not writeable
    Collecting seaborn
      Downloading seaborn-0.11.1-py3-none-any.whl (285 kB)
    [K     |████████████████████████████████| 285 kB 6.4 MB/s eta 0:00:01
    [?25hRequirement already satisfied: numpy>=1.15 in /Library/Frameworks/Python.framework/Versions/3.8/lib/python3.8/site-packages (from seaborn) (1.20.2)
    Requirement already satisfied: pandas>=0.23 in /Library/Frameworks/Python.framework/Versions/3.8/lib/python3.8/site-packages (from seaborn) (1.2.3)
    Collecting scipy>=1.0
      Downloading scipy-1.7.0-cp38-cp38-macosx_10_9_x86_64.whl (31.9 MB)
    [K     |████████████████████████████████| 31.9 MB 15.6 MB/s eta 0:00:01   |███████▌                        | 7.4 MB 5.1 MB/s eta 0:00:05     |█████████████████████████████   | 29.1 MB 15.6 MB/s eta 0:00:01
    [?25hCollecting matplotlib>=2.2
      Downloading matplotlib-3.4.2-cp38-cp38-macosx_10_9_x86_64.whl (7.2 MB)
    [K     |████████████████████████████████| 7.2 MB 8.6 MB/s eta 0:00:01
    [?25hCollecting kiwisolver>=1.0.1
      Downloading kiwisolver-1.3.1-cp38-cp38-macosx_10_9_x86_64.whl (61 kB)
    [K     |████████████████████████████████| 61 kB 273 kB/s  eta 0:00:01
    [?25hCollecting cycler>=0.10
      Downloading cycler-0.10.0-py2.py3-none-any.whl (6.5 kB)
    Collecting pillow>=6.2.0
      Downloading Pillow-8.2.0-cp38-cp38-macosx_10_10_x86_64.whl (2.8 MB)
    [K     |████████████████████████████████| 2.8 MB 14.6 MB/s eta 0:00:01
    [?25hRequirement already satisfied: python-dateutil>=2.7 in /Library/Frameworks/Python.framework/Versions/3.8/lib/python3.8/site-packages (from matplotlib>=2.2->seaborn) (2.8.1)
    Requirement already satisfied: pyparsing>=2.2.1 in /Library/Frameworks/Python.framework/Versions/3.8/lib/python3.8/site-packages (from matplotlib>=2.2->seaborn) (2.4.7)
    Requirement already satisfied: six in /Library/Frameworks/Python.framework/Versions/3.8/lib/python3.8/site-packages (from cycler>=0.10->matplotlib>=2.2->seaborn) (1.15.0)
    Requirement already satisfied: pytz>=2017.3 in /Library/Frameworks/Python.framework/Versions/3.8/lib/python3.8/site-packages (from pandas>=0.23->seaborn) (2021.1)
    Installing collected packages: pillow, kiwisolver, cycler, scipy, matplotlib, seaborn
    Successfully installed cycler-0.10.0 kiwisolver-1.3.1 matplotlib-3.4.2 pillow-8.2.0 scipy-1.7.0 seaborn-0.11.1
    [33mWARNING: You are using pip version 21.0.1; however, version 21.1.2 is available.
    You should consider upgrading via the '/usr/local/bin/python3 -m pip install --upgrade pip' command.[0m
    Note: you may need to restart the kernel to use updated packages.



```python
# Import libraries

import pandas as pd
import seaborn as sns
import numpy as np

import matplotlib
import matplotlib.pyplot as plt
plt.style.use('ggplot')
from matplotlib.pyplot import figure

%matplotlib inline
matplotlib.rcParams['figure.figsize'] = (12, 8) # Adjusts the configuration of the plots we'll create

# Read in the data

df = pd.read_csv('/Users/dwhite/Downloads/movies.csv')
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
      <th>budget</th>
      <th>company</th>
      <th>country</th>
      <th>director</th>
      <th>genre</th>
      <th>gross</th>
      <th>name</th>
      <th>rating</th>
      <th>released</th>
      <th>runtime</th>
      <th>score</th>
      <th>star</th>
      <th>votes</th>
      <th>writer</th>
      <th>year</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>8000000.0</td>
      <td>Columbia Pictures Corporation</td>
      <td>USA</td>
      <td>Rob Reiner</td>
      <td>Adventure</td>
      <td>52287414.0</td>
      <td>Stand by Me</td>
      <td>R</td>
      <td>1986-08-22</td>
      <td>89</td>
      <td>8.1</td>
      <td>Wil Wheaton</td>
      <td>299174</td>
      <td>Stephen King</td>
      <td>1986</td>
    </tr>
    <tr>
      <th>1</th>
      <td>6000000.0</td>
      <td>Paramount Pictures</td>
      <td>USA</td>
      <td>John Hughes</td>
      <td>Comedy</td>
      <td>70136369.0</td>
      <td>Ferris Bueller's Day Off</td>
      <td>PG-13</td>
      <td>1986-06-11</td>
      <td>103</td>
      <td>7.8</td>
      <td>Matthew Broderick</td>
      <td>264740</td>
      <td>John Hughes</td>
      <td>1986</td>
    </tr>
    <tr>
      <th>2</th>
      <td>15000000.0</td>
      <td>Paramount Pictures</td>
      <td>USA</td>
      <td>Tony Scott</td>
      <td>Action</td>
      <td>179800601.0</td>
      <td>Top Gun</td>
      <td>PG</td>
      <td>1986-05-16</td>
      <td>110</td>
      <td>6.9</td>
      <td>Tom Cruise</td>
      <td>236909</td>
      <td>Jim Cash</td>
      <td>1986</td>
    </tr>
    <tr>
      <th>3</th>
      <td>18500000.0</td>
      <td>Twentieth Century Fox Film Corporation</td>
      <td>USA</td>
      <td>James Cameron</td>
      <td>Action</td>
      <td>85160248.0</td>
      <td>Aliens</td>
      <td>R</td>
      <td>1986-07-18</td>
      <td>137</td>
      <td>8.4</td>
      <td>Sigourney Weaver</td>
      <td>540152</td>
      <td>James Cameron</td>
      <td>1986</td>
    </tr>
    <tr>
      <th>4</th>
      <td>9000000.0</td>
      <td>Walt Disney Pictures</td>
      <td>USA</td>
      <td>Randal Kleiser</td>
      <td>Adventure</td>
      <td>18564613.0</td>
      <td>Flight of the Navigator</td>
      <td>PG</td>
      <td>1986-08-01</td>
      <td>90</td>
      <td>6.9</td>
      <td>Joey Cramer</td>
      <td>36636</td>
      <td>Mark H. Baker</td>
      <td>1986</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Checking for missing data

for col in df.columns:
    pct_missing = np.mean(df[col].isnull())
    print('{} - {}%'.format(col, pct_missing))
```

    budget - 0.0%
    company - 0.0%
    country - 0.0%
    director - 0.0%
    genre - 0.0%
    gross - 0.0%
    name - 0.0%
    rating - 0.0%
    released - 0.0%
    runtime - 0.0%
    score - 0.0%
    star - 0.0%
    votes - 0.0%
    writer - 0.0%
    year - 0.0%



```python
# Data types for our columns

df.dtypes
```




    budget      float64
    company      object
    country      object
    director     object
    genre        object
    gross       float64
    name         object
    rating       object
    released     object
    runtime       int64
    score       float64
    star         object
    votes         int64
    writer       object
    year          int64
    dtype: object




```python
# Changing data types of budget and gross columns from floats to integers

df['budget'] = df['budget'].astype('int64')
df['gross'] = df['gross'].astype('int64')
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
      <th>budget</th>
      <th>company</th>
      <th>country</th>
      <th>director</th>
      <th>genre</th>
      <th>gross</th>
      <th>name</th>
      <th>rating</th>
      <th>released</th>
      <th>runtime</th>
      <th>score</th>
      <th>star</th>
      <th>votes</th>
      <th>writer</th>
      <th>year</th>
      <th>yearcorrect</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>6380</th>
      <td>245000000.0</td>
      <td>1428</td>
      <td>54</td>
      <td>1037</td>
      <td>0</td>
      <td>936662225.0</td>
      <td>4679</td>
      <td>7</td>
      <td>2290</td>
      <td>136</td>
      <td>8.1</td>
      <td>475</td>
      <td>687192</td>
      <td>2356</td>
      <td>2015</td>
      <td>2290</td>
    </tr>
    <tr>
      <th>5061</th>
      <td>237000000.0</td>
      <td>2062</td>
      <td>53</td>
      <td>1066</td>
      <td>0</td>
      <td>760507625.0</td>
      <td>501</td>
      <td>7</td>
      <td>1800</td>
      <td>162</td>
      <td>7.8</td>
      <td>2084</td>
      <td>954412</td>
      <td>1629</td>
      <td>2009</td>
      <td>1800</td>
    </tr>
    <tr>
      <th>2420</th>
      <td>200000000.0</td>
      <td>2062</td>
      <td>54</td>
      <td>1066</td>
      <td>6</td>
      <td>658672302.0</td>
      <td>6177</td>
      <td>7</td>
      <td>910</td>
      <td>194</td>
      <td>7.8</td>
      <td>1444</td>
      <td>862554</td>
      <td>1629</td>
      <td>1997</td>
      <td>910</td>
    </tr>
    <tr>
      <th>6391</th>
      <td>150000000.0</td>
      <td>2085</td>
      <td>54</td>
      <td>466</td>
      <td>0</td>
      <td>652270625.0</td>
      <td>2721</td>
      <td>7</td>
      <td>2247</td>
      <td>124</td>
      <td>7.0</td>
      <td>404</td>
      <td>469200</td>
      <td>3310</td>
      <td>2015</td>
      <td>2247</td>
    </tr>
    <tr>
      <th>5723</th>
      <td>220000000.0</td>
      <td>1491</td>
      <td>54</td>
      <td>1412</td>
      <td>0</td>
      <td>623357910.0</td>
      <td>4995</td>
      <td>7</td>
      <td>1987</td>
      <td>143</td>
      <td>8.1</td>
      <td>2001</td>
      <td>1064633</td>
      <td>2145</td>
      <td>2012</td>
      <td>1987</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Create column for the correct year

df['yearcorrect'] = df['released'].astype(str).str[:4]

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
      <th>budget</th>
      <th>company</th>
      <th>country</th>
      <th>director</th>
      <th>genre</th>
      <th>gross</th>
      <th>name</th>
      <th>rating</th>
      <th>released</th>
      <th>runtime</th>
      <th>score</th>
      <th>star</th>
      <th>votes</th>
      <th>writer</th>
      <th>year</th>
      <th>yearcorrect</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>6380</th>
      <td>245000000.0</td>
      <td>1428</td>
      <td>54</td>
      <td>1037</td>
      <td>0</td>
      <td>936662225.0</td>
      <td>4679</td>
      <td>7</td>
      <td>2290</td>
      <td>136</td>
      <td>8.1</td>
      <td>475</td>
      <td>687192</td>
      <td>2356</td>
      <td>2015</td>
      <td>2290</td>
    </tr>
    <tr>
      <th>5061</th>
      <td>237000000.0</td>
      <td>2062</td>
      <td>53</td>
      <td>1066</td>
      <td>0</td>
      <td>760507625.0</td>
      <td>501</td>
      <td>7</td>
      <td>1800</td>
      <td>162</td>
      <td>7.8</td>
      <td>2084</td>
      <td>954412</td>
      <td>1629</td>
      <td>2009</td>
      <td>1800</td>
    </tr>
    <tr>
      <th>2420</th>
      <td>200000000.0</td>
      <td>2062</td>
      <td>54</td>
      <td>1066</td>
      <td>6</td>
      <td>658672302.0</td>
      <td>6177</td>
      <td>7</td>
      <td>910</td>
      <td>194</td>
      <td>7.8</td>
      <td>1444</td>
      <td>862554</td>
      <td>1629</td>
      <td>1997</td>
      <td>910</td>
    </tr>
    <tr>
      <th>6391</th>
      <td>150000000.0</td>
      <td>2085</td>
      <td>54</td>
      <td>466</td>
      <td>0</td>
      <td>652270625.0</td>
      <td>2721</td>
      <td>7</td>
      <td>2247</td>
      <td>124</td>
      <td>7.0</td>
      <td>404</td>
      <td>469200</td>
      <td>3310</td>
      <td>2015</td>
      <td>2247</td>
    </tr>
    <tr>
      <th>5723</th>
      <td>220000000.0</td>
      <td>1491</td>
      <td>54</td>
      <td>1412</td>
      <td>0</td>
      <td>623357910.0</td>
      <td>4995</td>
      <td>7</td>
      <td>1987</td>
      <td>143</td>
      <td>8.1</td>
      <td>2001</td>
      <td>1064633</td>
      <td>2145</td>
      <td>2012</td>
      <td>1987</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.sort_values(by = ['gross'], inplace = False, ascending = False)

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
      <th>budget</th>
      <th>company</th>
      <th>country</th>
      <th>director</th>
      <th>genre</th>
      <th>gross</th>
      <th>name</th>
      <th>rating</th>
      <th>released</th>
      <th>runtime</th>
      <th>score</th>
      <th>star</th>
      <th>votes</th>
      <th>writer</th>
      <th>year</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>6380</th>
      <td>245000000.0</td>
      <td>1428</td>
      <td>54</td>
      <td>1037</td>
      <td>0</td>
      <td>936662225.0</td>
      <td>4679</td>
      <td>7</td>
      <td>2290</td>
      <td>136</td>
      <td>8.1</td>
      <td>475</td>
      <td>687192</td>
      <td>2356</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>5061</th>
      <td>237000000.0</td>
      <td>2062</td>
      <td>53</td>
      <td>1066</td>
      <td>0</td>
      <td>760507625.0</td>
      <td>501</td>
      <td>7</td>
      <td>1800</td>
      <td>162</td>
      <td>7.8</td>
      <td>2084</td>
      <td>954412</td>
      <td>1629</td>
      <td>2009</td>
    </tr>
    <tr>
      <th>2420</th>
      <td>200000000.0</td>
      <td>2062</td>
      <td>54</td>
      <td>1066</td>
      <td>6</td>
      <td>658672302.0</td>
      <td>6177</td>
      <td>7</td>
      <td>910</td>
      <td>194</td>
      <td>7.8</td>
      <td>1444</td>
      <td>862554</td>
      <td>1629</td>
      <td>1997</td>
    </tr>
    <tr>
      <th>6391</th>
      <td>150000000.0</td>
      <td>2085</td>
      <td>54</td>
      <td>466</td>
      <td>0</td>
      <td>652270625.0</td>
      <td>2721</td>
      <td>7</td>
      <td>2247</td>
      <td>124</td>
      <td>7.0</td>
      <td>404</td>
      <td>469200</td>
      <td>3310</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>5723</th>
      <td>220000000.0</td>
      <td>1491</td>
      <td>54</td>
      <td>1412</td>
      <td>0</td>
      <td>623357910.0</td>
      <td>4995</td>
      <td>7</td>
      <td>1987</td>
      <td>143</td>
      <td>8.1</td>
      <td>2001</td>
      <td>1064633</td>
      <td>2145</td>
      <td>2012</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Makes the df scrollable

pd.set_option('display.max_rows', None)
```


```python
# Drop duplicates, if they exist

df.drop_duplicates()

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
      <th>budget</th>
      <th>company</th>
      <th>country</th>
      <th>director</th>
      <th>genre</th>
      <th>gross</th>
      <th>name</th>
      <th>rating</th>
      <th>released</th>
      <th>runtime</th>
      <th>score</th>
      <th>star</th>
      <th>votes</th>
      <th>writer</th>
      <th>year</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>6380</th>
      <td>245000000.0</td>
      <td>1428</td>
      <td>54</td>
      <td>1037</td>
      <td>0</td>
      <td>936662225.0</td>
      <td>4679</td>
      <td>7</td>
      <td>2290</td>
      <td>136</td>
      <td>8.1</td>
      <td>475</td>
      <td>687192</td>
      <td>2356</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>5061</th>
      <td>237000000.0</td>
      <td>2062</td>
      <td>53</td>
      <td>1066</td>
      <td>0</td>
      <td>760507625.0</td>
      <td>501</td>
      <td>7</td>
      <td>1800</td>
      <td>162</td>
      <td>7.8</td>
      <td>2084</td>
      <td>954412</td>
      <td>1629</td>
      <td>2009</td>
    </tr>
    <tr>
      <th>2420</th>
      <td>200000000.0</td>
      <td>2062</td>
      <td>54</td>
      <td>1066</td>
      <td>6</td>
      <td>658672302.0</td>
      <td>6177</td>
      <td>7</td>
      <td>910</td>
      <td>194</td>
      <td>7.8</td>
      <td>1444</td>
      <td>862554</td>
      <td>1629</td>
      <td>1997</td>
    </tr>
    <tr>
      <th>6391</th>
      <td>150000000.0</td>
      <td>2085</td>
      <td>54</td>
      <td>466</td>
      <td>0</td>
      <td>652270625.0</td>
      <td>2721</td>
      <td>7</td>
      <td>2247</td>
      <td>124</td>
      <td>7.0</td>
      <td>404</td>
      <td>469200</td>
      <td>3310</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>5723</th>
      <td>220000000.0</td>
      <td>1491</td>
      <td>54</td>
      <td>1412</td>
      <td>0</td>
      <td>623357910.0</td>
      <td>4995</td>
      <td>7</td>
      <td>1987</td>
      <td>143</td>
      <td>8.1</td>
      <td>2001</td>
      <td>1064633</td>
      <td>2145</td>
      <td>2012</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.sort_values(by = ['gross'], inplace = False, ascending = False)

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
      <th>budget</th>
      <th>company</th>
      <th>country</th>
      <th>director</th>
      <th>genre</th>
      <th>gross</th>
      <th>name</th>
      <th>rating</th>
      <th>released</th>
      <th>runtime</th>
      <th>score</th>
      <th>star</th>
      <th>votes</th>
      <th>writer</th>
      <th>year</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>6380</th>
      <td>245000000.0</td>
      <td>1428</td>
      <td>54</td>
      <td>1037</td>
      <td>0</td>
      <td>936662225.0</td>
      <td>4679</td>
      <td>7</td>
      <td>2290</td>
      <td>136</td>
      <td>8.1</td>
      <td>475</td>
      <td>687192</td>
      <td>2356</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>5061</th>
      <td>237000000.0</td>
      <td>2062</td>
      <td>53</td>
      <td>1066</td>
      <td>0</td>
      <td>760507625.0</td>
      <td>501</td>
      <td>7</td>
      <td>1800</td>
      <td>162</td>
      <td>7.8</td>
      <td>2084</td>
      <td>954412</td>
      <td>1629</td>
      <td>2009</td>
    </tr>
    <tr>
      <th>2420</th>
      <td>200000000.0</td>
      <td>2062</td>
      <td>54</td>
      <td>1066</td>
      <td>6</td>
      <td>658672302.0</td>
      <td>6177</td>
      <td>7</td>
      <td>910</td>
      <td>194</td>
      <td>7.8</td>
      <td>1444</td>
      <td>862554</td>
      <td>1629</td>
      <td>1997</td>
    </tr>
    <tr>
      <th>6391</th>
      <td>150000000.0</td>
      <td>2085</td>
      <td>54</td>
      <td>466</td>
      <td>0</td>
      <td>652270625.0</td>
      <td>2721</td>
      <td>7</td>
      <td>2247</td>
      <td>124</td>
      <td>7.0</td>
      <td>404</td>
      <td>469200</td>
      <td>3310</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>5723</th>
      <td>220000000.0</td>
      <td>1491</td>
      <td>54</td>
      <td>1412</td>
      <td>0</td>
      <td>623357910.0</td>
      <td>4995</td>
      <td>7</td>
      <td>1987</td>
      <td>143</td>
      <td>8.1</td>
      <td>2001</td>
      <td>1064633</td>
      <td>2145</td>
      <td>2012</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Scatterplot comparing budget and gross using matplotlib

plt.scatter(x = df['budget'], y = df['gross'])

plt.title('Budget vs. Gross Earnings')
plt.xlabel('Gross Earnings')
plt.ylabel('Budget for Film')
plt.show()
```


    
![png](Movie%20Correlation%20Project_files/Movie%20Correlation%20Project_12_0.png)
    



```python
# Plot budget vs. gross using seaborn

sns.regplot(x = 'budget', y = 'gross', data = df, scatter_kws = {'color': 'red'}, line_kws = {'color': 'blue'})
```




    <AxesSubplot:xlabel='budget', ylabel='gross'>




    
![png](Movie%20Correlation%20Project_files/Movie%20Correlation%20Project_13_1.png)
    



```python
# Beginning to look at correlation

df.corr()
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
      <th>budget</th>
      <th>gross</th>
      <th>runtime</th>
      <th>score</th>
      <th>votes</th>
      <th>year</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>budget</th>
      <td>1.000000</td>
      <td>0.712196</td>
      <td>0.268226</td>
      <td>0.042145</td>
      <td>0.503924</td>
      <td>0.291009</td>
    </tr>
    <tr>
      <th>gross</th>
      <td>0.712196</td>
      <td>1.000000</td>
      <td>0.224579</td>
      <td>0.165693</td>
      <td>0.662457</td>
      <td>0.191548</td>
    </tr>
    <tr>
      <th>runtime</th>
      <td>0.268226</td>
      <td>0.224579</td>
      <td>1.000000</td>
      <td>0.395343</td>
      <td>0.317399</td>
      <td>0.087639</td>
    </tr>
    <tr>
      <th>score</th>
      <td>0.042145</td>
      <td>0.165693</td>
      <td>0.395343</td>
      <td>1.000000</td>
      <td>0.393607</td>
      <td>0.105276</td>
    </tr>
    <tr>
      <th>votes</th>
      <td>0.503924</td>
      <td>0.662457</td>
      <td>0.317399</td>
      <td>0.393607</td>
      <td>1.000000</td>
      <td>0.229304</td>
    </tr>
    <tr>
      <th>year</th>
      <td>0.291009</td>
      <td>0.191548</td>
      <td>0.087639</td>
      <td>0.105276</td>
      <td>0.229304</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
correlation_matrix = df.corr()

sns.heatmap(correlation_matrix, annot = True)

plt.title('Correlation Matrix for Numeric Features')

plt.xlabel('Movie Features')

plt.ylabel('Movie Features')

plt.show()
```


    
![png](Movie%20Correlation%20Project_files/Movie%20Correlation%20Project_15_0.png)
    



```python
# Looking at company

df = df.sort_values(by = ['gross'], inplace = False, ascending = False)

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
      <th>budget</th>
      <th>company</th>
      <th>country</th>
      <th>director</th>
      <th>genre</th>
      <th>gross</th>
      <th>name</th>
      <th>rating</th>
      <th>released</th>
      <th>runtime</th>
      <th>score</th>
      <th>star</th>
      <th>votes</th>
      <th>writer</th>
      <th>year</th>
      <th>yearcorrect</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>6380</th>
      <td>245000000</td>
      <td>Lucasfilm</td>
      <td>USA</td>
      <td>J.J. Abrams</td>
      <td>Action</td>
      <td>936662225</td>
      <td>Star Wars: The Force Awakens</td>
      <td>PG-13</td>
      <td>2015-12-18</td>
      <td>136</td>
      <td>8.1</td>
      <td>Daisy Ridley</td>
      <td>687192</td>
      <td>Lawrence Kasdan</td>
      <td>2015</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>5061</th>
      <td>237000000</td>
      <td>Twentieth Century Fox Film Corporation</td>
      <td>UK</td>
      <td>James Cameron</td>
      <td>Action</td>
      <td>760507625</td>
      <td>Avatar</td>
      <td>PG-13</td>
      <td>2009-12-18</td>
      <td>162</td>
      <td>7.8</td>
      <td>Sam Worthington</td>
      <td>954412</td>
      <td>James Cameron</td>
      <td>2009</td>
      <td>2009</td>
    </tr>
    <tr>
      <th>2420</th>
      <td>200000000</td>
      <td>Twentieth Century Fox Film Corporation</td>
      <td>USA</td>
      <td>James Cameron</td>
      <td>Drama</td>
      <td>658672302</td>
      <td>Titanic</td>
      <td>PG-13</td>
      <td>1997-12-19</td>
      <td>194</td>
      <td>7.8</td>
      <td>Leonardo DiCaprio</td>
      <td>862554</td>
      <td>James Cameron</td>
      <td>1997</td>
      <td>1997</td>
    </tr>
    <tr>
      <th>6391</th>
      <td>150000000</td>
      <td>Universal Pictures</td>
      <td>USA</td>
      <td>Colin Trevorrow</td>
      <td>Action</td>
      <td>652270625</td>
      <td>Jurassic World</td>
      <td>PG-13</td>
      <td>2015-06-12</td>
      <td>124</td>
      <td>7.0</td>
      <td>Chris Pratt</td>
      <td>469200</td>
      <td>Rick Jaffa</td>
      <td>2015</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>5723</th>
      <td>220000000</td>
      <td>Marvel Studios</td>
      <td>USA</td>
      <td>Joss Whedon</td>
      <td>Action</td>
      <td>623357910</td>
      <td>The Avengers</td>
      <td>PG-13</td>
      <td>2012-05-04</td>
      <td>143</td>
      <td>8.1</td>
      <td>Robert Downey Jr.</td>
      <td>1064633</td>
      <td>Joss Whedon</td>
      <td>2012</td>
      <td>2012</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_numerized = df

for col_name in df_numerized.columns:
    if(df_numerized[col_name].dtype == 'object'):
        df_numerized[col_name] = df_numerized[col_name].astype('category')
        df_numerized[col_name] = df_numerized[col_name].cat.codes
        

        
df_numerized.head()
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
      <th>budget</th>
      <th>company</th>
      <th>country</th>
      <th>director</th>
      <th>genre</th>
      <th>gross</th>
      <th>name</th>
      <th>rating</th>
      <th>released</th>
      <th>runtime</th>
      <th>score</th>
      <th>star</th>
      <th>votes</th>
      <th>writer</th>
      <th>year</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>6380</th>
      <td>245000000.0</td>
      <td>1428</td>
      <td>54</td>
      <td>1037</td>
      <td>0</td>
      <td>936662225.0</td>
      <td>4679</td>
      <td>7</td>
      <td>2290</td>
      <td>136</td>
      <td>8.1</td>
      <td>475</td>
      <td>687192</td>
      <td>2356</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>5061</th>
      <td>237000000.0</td>
      <td>2062</td>
      <td>53</td>
      <td>1066</td>
      <td>0</td>
      <td>760507625.0</td>
      <td>501</td>
      <td>7</td>
      <td>1800</td>
      <td>162</td>
      <td>7.8</td>
      <td>2084</td>
      <td>954412</td>
      <td>1629</td>
      <td>2009</td>
    </tr>
    <tr>
      <th>2420</th>
      <td>200000000.0</td>
      <td>2062</td>
      <td>54</td>
      <td>1066</td>
      <td>6</td>
      <td>658672302.0</td>
      <td>6177</td>
      <td>7</td>
      <td>910</td>
      <td>194</td>
      <td>7.8</td>
      <td>1444</td>
      <td>862554</td>
      <td>1629</td>
      <td>1997</td>
    </tr>
    <tr>
      <th>6391</th>
      <td>150000000.0</td>
      <td>2085</td>
      <td>54</td>
      <td>466</td>
      <td>0</td>
      <td>652270625.0</td>
      <td>2721</td>
      <td>7</td>
      <td>2247</td>
      <td>124</td>
      <td>7.0</td>
      <td>404</td>
      <td>469200</td>
      <td>3310</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>5723</th>
      <td>220000000.0</td>
      <td>1491</td>
      <td>54</td>
      <td>1412</td>
      <td>0</td>
      <td>623357910.0</td>
      <td>4995</td>
      <td>7</td>
      <td>1987</td>
      <td>143</td>
      <td>8.1</td>
      <td>2001</td>
      <td>1064633</td>
      <td>2145</td>
      <td>2012</td>
    </tr>
  </tbody>
</table>
</div>




```python
df = df.sort_values(by = ['gross'], inplace = False, ascending = False)

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
      <th>budget</th>
      <th>company</th>
      <th>country</th>
      <th>director</th>
      <th>genre</th>
      <th>gross</th>
      <th>name</th>
      <th>rating</th>
      <th>released</th>
      <th>runtime</th>
      <th>score</th>
      <th>star</th>
      <th>votes</th>
      <th>writer</th>
      <th>year</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>6380</th>
      <td>245000000.0</td>
      <td>Lucasfilm</td>
      <td>USA</td>
      <td>J.J. Abrams</td>
      <td>Action</td>
      <td>936662225.0</td>
      <td>Star Wars: The Force Awakens</td>
      <td>PG-13</td>
      <td>2015-12-18</td>
      <td>136</td>
      <td>8.1</td>
      <td>Daisy Ridley</td>
      <td>687192</td>
      <td>Lawrence Kasdan</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>5061</th>
      <td>237000000.0</td>
      <td>Twentieth Century Fox Film Corporation</td>
      <td>UK</td>
      <td>James Cameron</td>
      <td>Action</td>
      <td>760507625.0</td>
      <td>Avatar</td>
      <td>PG-13</td>
      <td>2009-12-18</td>
      <td>162</td>
      <td>7.8</td>
      <td>Sam Worthington</td>
      <td>954412</td>
      <td>James Cameron</td>
      <td>2009</td>
    </tr>
    <tr>
      <th>2420</th>
      <td>200000000.0</td>
      <td>Twentieth Century Fox Film Corporation</td>
      <td>USA</td>
      <td>James Cameron</td>
      <td>Drama</td>
      <td>658672302.0</td>
      <td>Titanic</td>
      <td>PG-13</td>
      <td>1997-12-19</td>
      <td>194</td>
      <td>7.8</td>
      <td>Leonardo DiCaprio</td>
      <td>862554</td>
      <td>James Cameron</td>
      <td>1997</td>
    </tr>
    <tr>
      <th>6391</th>
      <td>150000000.0</td>
      <td>Universal Pictures</td>
      <td>USA</td>
      <td>Colin Trevorrow</td>
      <td>Action</td>
      <td>652270625.0</td>
      <td>Jurassic World</td>
      <td>PG-13</td>
      <td>2015-06-12</td>
      <td>124</td>
      <td>7.0</td>
      <td>Chris Pratt</td>
      <td>469200</td>
      <td>Rick Jaffa</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>5723</th>
      <td>220000000.0</td>
      <td>Marvel Studios</td>
      <td>USA</td>
      <td>Joss Whedon</td>
      <td>Action</td>
      <td>623357910.0</td>
      <td>The Avengers</td>
      <td>PG-13</td>
      <td>2012-05-04</td>
      <td>143</td>
      <td>8.1</td>
      <td>Robert Downey Jr.</td>
      <td>1064633</td>
      <td>Joss Whedon</td>
      <td>2012</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_numerized.head()
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
      <th>budget</th>
      <th>company</th>
      <th>country</th>
      <th>director</th>
      <th>genre</th>
      <th>gross</th>
      <th>name</th>
      <th>rating</th>
      <th>released</th>
      <th>runtime</th>
      <th>score</th>
      <th>star</th>
      <th>votes</th>
      <th>writer</th>
      <th>year</th>
      <th>yearcorrect</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>6380</th>
      <td>245000000</td>
      <td>1428</td>
      <td>54</td>
      <td>1037</td>
      <td>0</td>
      <td>936662225</td>
      <td>4679</td>
      <td>7</td>
      <td>2290</td>
      <td>136</td>
      <td>8.1</td>
      <td>475</td>
      <td>687192</td>
      <td>2356</td>
      <td>2015</td>
      <td>29</td>
    </tr>
    <tr>
      <th>5061</th>
      <td>237000000</td>
      <td>2062</td>
      <td>53</td>
      <td>1066</td>
      <td>0</td>
      <td>760507625</td>
      <td>501</td>
      <td>7</td>
      <td>1800</td>
      <td>162</td>
      <td>7.8</td>
      <td>2084</td>
      <td>954412</td>
      <td>1629</td>
      <td>2009</td>
      <td>23</td>
    </tr>
    <tr>
      <th>2420</th>
      <td>200000000</td>
      <td>2062</td>
      <td>54</td>
      <td>1066</td>
      <td>6</td>
      <td>658672302</td>
      <td>6177</td>
      <td>7</td>
      <td>910</td>
      <td>194</td>
      <td>7.8</td>
      <td>1444</td>
      <td>862554</td>
      <td>1629</td>
      <td>1997</td>
      <td>11</td>
    </tr>
    <tr>
      <th>6391</th>
      <td>150000000</td>
      <td>2085</td>
      <td>54</td>
      <td>466</td>
      <td>0</td>
      <td>652270625</td>
      <td>2721</td>
      <td>7</td>
      <td>2247</td>
      <td>124</td>
      <td>7.0</td>
      <td>404</td>
      <td>469200</td>
      <td>3310</td>
      <td>2015</td>
      <td>29</td>
    </tr>
    <tr>
      <th>5723</th>
      <td>220000000</td>
      <td>1491</td>
      <td>54</td>
      <td>1412</td>
      <td>0</td>
      <td>623357910</td>
      <td>4995</td>
      <td>7</td>
      <td>1987</td>
      <td>143</td>
      <td>8.1</td>
      <td>2001</td>
      <td>1064633</td>
      <td>2145</td>
      <td>2012</td>
      <td>26</td>
    </tr>
  </tbody>
</table>
</div>




```python
correlation_matrix = df_numerized.corr()

sns.heatmap(correlation_matrix, annot = True)

plt.title('Correlation Matrix for Numeric Features')

plt.xlabel('Movie Features')

plt.ylabel('Movie Features')

plt.show()
```


    
![png](Movie%20Correlation%20Project_files/Movie%20Correlation%20Project_20_0.png)
    



```python
correlation_mat = df_numerized.corr()

corr_pairs = correlation_mat.unstack()

corr_pairs.head()
```




    budget  budget      1.000000
            company     0.187205
            country     0.137635
            director    0.011602
            genre      -0.346794
    dtype: float64




```python
sorted_pairs = corr_pairs.sort_values()

sorted_pairs.head()
```




    budget   genre    -0.346794
    genre    budget   -0.346794
             gross    -0.242676
    gross    genre    -0.242676
    country  score    -0.174414
    dtype: float64




```python
high_corr = sorted_pairs[(sorted_pairs) > 0.5]

high_corr
```




    votes        budget         0.503924
    budget       votes          0.503924
    votes        gross          0.662457
    gross        votes          0.662457
                 budget         0.712196
    budget       gross          0.712196
    released     year           0.996187
    year         released       0.996187
    yearcorrect  year           0.996229
    year         yearcorrect    0.996229
    yearcorrect  released       0.999389
    released     yearcorrect    0.999389
    budget       budget         1.000000
    writer       writer         1.000000
    votes        votes          1.000000
    star         star           1.000000
    score        score          1.000000
    runtime      runtime        1.000000
    released     released       1.000000
    rating       rating         1.000000
    name         name           1.000000
    gross        gross          1.000000
    genre        genre          1.000000
    director     director       1.000000
    country      country        1.000000
    company      company        1.000000
    year         year           1.000000
    yearcorrect  yearcorrect    1.000000
    dtype: float64




```python
# We see from the unstacked list that votes and budget have the highest correlation to gross earnings

# The company has a low correlation after all
```
