
#  Beta Calculator
## Author : Avnit Bambah
### Date : 03/12/2018
###### Learning ML with python 3 on Pluralsight.
###### Predicting stock beta


```python
import pandas as pd
import matplotlib as plt
import numpy as np
from pandas_datareader import data
import googlefinance
import matplotlib.pyplot as plt

# do ploting inline instead of seperate windows
%matplotlib inline
```


```python
# add new stocks to the csv file
df = pd.read_csv("./holdings-xlk.csv")
```


```python
# Define the instruments to download. We would like to see Apple, Microsoft and the S&P500 index in addition to the one in the csv file
tickers = ['AAPL', 'MSFT', 'SPY','CME','GOOG','VVI','agg']
# get the symbols and add them to the list
symbols = df.iloc[:,[0]]
array = symbols.values.tolist()
for i in range(1 , len(array)):
    tickers.append(str(array[i]).replace('[\'', '').replace('\']',''))
tickers
```




    ['AAPL',
     'MSFT',
     'SPY',
     'CME',
     'GOOG',
     'VVI',
     'agg',
     'BETR',
     'BUFF',
     'CALM',
     'CENT',
     'DTEA',
     'FRPT',
     'KHC',
     'LANC',
     'LWAY',
     'NUTR',
     'PF',
     'POST',
     'PPC',
     'RELV',
     'RIBT',
     'SAFM',
     'TOF',
     'WILC',
     'WWAV']




```python

# Define which online source one should use
data_source = 'yahoo'

# We would like all available data from 01/01/2000 until 12/31/2018.
start_date = '2000-01-01'
end_date = '2018-03-24'

# User pandas_reader.data.DataReader to load the desired data. As simple as that.
try:
    panel_data = data.DataReader(tickers, data_source, start_date, end_date)
except:
    print('error in the symbol')
#del panel_data["2017-01-02"]

# Getting just the adjusted closing prices. This will return a Pandas DataFrame
# The index in this DataFrame is the major index of the panel_data.
close = panel_data.loc['Adj Close']

close.dropna(axis=0, how='any')

# Getting all weekdays between start date and end date
all_weekdays = pd.date_range(start=start_date, end=end_date, freq='B')

# How do we align the existing prices in adj_close with our new set of dates?
# All we need to do is reindex close using all_weekdays as the new index
close = close.reindex(all_weekdays)

close_onedayold = close.shift(-1)
close_onedayold.head(10)

close_final = ((close / close_onedayold) -1) * 100

```

    /Users/avnitbambah/anaconda3/lib/python3.6/site-packages/pandas_datareader/yahoo/daily.py:136: SymbolWarning: Failed to read symbol: 'NUTR', replacing with NaN.
      warnings.warn(msg.format(sym), SymbolWarning)
    /Users/avnitbambah/anaconda3/lib/python3.6/site-packages/pandas_datareader/yahoo/daily.py:136: SymbolWarning: Failed to read symbol: 'TOF', replacing with NaN.
      warnings.warn(msg.format(sym), SymbolWarning)
    /Users/avnitbambah/anaconda3/lib/python3.6/site-packages/pandas_datareader/yahoo/daily.py:136: SymbolWarning: Failed to read symbol: 'WWAV', replacing with NaN.
      warnings.warn(msg.format(sym), SymbolWarning)



```python
close_onedayold.head(10)
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
      <th>AAPL</th>
      <th>BETR</th>
      <th>BUFF</th>
      <th>CALM</th>
      <th>CENT</th>
      <th>CME</th>
      <th>DTEA</th>
      <th>FRPT</th>
      <th>GOOG</th>
      <th>KHC</th>
      <th>...</th>
      <th>PPC</th>
      <th>RELV</th>
      <th>RIBT</th>
      <th>SAFM</th>
      <th>SPY</th>
      <th>TOF</th>
      <th>VVI</th>
      <th>WILC</th>
      <th>WWAV</th>
      <th>agg</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2000-01-03</th>
      <td>2.478144</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.604914</td>
      <td>3.286890</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>5.446455</td>
      <td>4.250875</td>
      <td>NaN</td>
      <td>4.003366</td>
      <td>99.349930</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-04</th>
      <td>2.514410</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.604914</td>
      <td>3.265820</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>5.504705</td>
      <td>4.000824</td>
      <td>NaN</td>
      <td>4.367311</td>
      <td>99.527641</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-05</th>
      <td>2.296816</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.626911</td>
      <td>3.286890</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>5.825084</td>
      <td>4.000824</td>
      <td>NaN</td>
      <td>4.124682</td>
      <td>97.928093</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-06</th>
      <td>2.405613</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.626911</td>
      <td>3.286890</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>5.970712</td>
      <td>3.875598</td>
      <td>NaN</td>
      <td>4.245998</td>
      <td>103.615379</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-07</th>
      <td>2.363304</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.626911</td>
      <td>3.202610</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>5.504705</td>
      <td>3.875598</td>
      <td>NaN</td>
      <td>4.124682</td>
      <td>103.970871</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-10</th>
      <td>2.242418</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.615912</td>
      <td>3.244750</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>5.533829</td>
      <td>4.250875</td>
      <td>NaN</td>
      <td>4.245998</td>
      <td>102.726746</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-11</th>
      <td>2.107934</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.615912</td>
      <td>3.329029</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>5.533829</td>
      <td>5.251082</td>
      <td>NaN</td>
      <td>3.912383</td>
      <td>101.704826</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-12</th>
      <td>2.339126</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.615912</td>
      <td>3.329029</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>5.970712</td>
      <td>5.001029</td>
      <td>NaN</td>
      <td>3.980611</td>
      <td>103.082207</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-13</th>
      <td>2.428280</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.621403</td>
      <td>3.202610</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>6.087214</td>
      <td>5.625959</td>
      <td>NaN</td>
      <td>4.306655</td>
      <td>104.481773</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-14</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>10 rows × 26 columns</p>
</div>




```python
close.head(10)
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
      <th>AAPL</th>
      <th>BETR</th>
      <th>BUFF</th>
      <th>CALM</th>
      <th>CENT</th>
      <th>CME</th>
      <th>DTEA</th>
      <th>FRPT</th>
      <th>GOOG</th>
      <th>KHC</th>
      <th>...</th>
      <th>PPC</th>
      <th>RELV</th>
      <th>RIBT</th>
      <th>SAFM</th>
      <th>SPY</th>
      <th>TOF</th>
      <th>VVI</th>
      <th>WILC</th>
      <th>WWAV</th>
      <th>agg</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2000-01-03</th>
      <td>2.706315</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.637909</td>
      <td>3.413309</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>5.883336</td>
      <td>4.125650</td>
      <td>NaN</td>
      <td>4.245998</td>
      <td>103.393242</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-04</th>
      <td>2.478144</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.604914</td>
      <td>3.286890</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>5.446455</td>
      <td>4.250875</td>
      <td>NaN</td>
      <td>4.003366</td>
      <td>99.349930</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-05</th>
      <td>2.514410</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.604914</td>
      <td>3.265820</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>5.504705</td>
      <td>4.000824</td>
      <td>NaN</td>
      <td>4.367311</td>
      <td>99.527641</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-06</th>
      <td>2.296816</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.626911</td>
      <td>3.286890</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>5.825084</td>
      <td>4.000824</td>
      <td>NaN</td>
      <td>4.124682</td>
      <td>97.928093</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-07</th>
      <td>2.405613</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.626911</td>
      <td>3.286890</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>5.970712</td>
      <td>3.875598</td>
      <td>NaN</td>
      <td>4.245998</td>
      <td>103.615379</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-10</th>
      <td>2.363304</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.626911</td>
      <td>3.202610</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>5.504705</td>
      <td>3.875598</td>
      <td>NaN</td>
      <td>4.124682</td>
      <td>103.970871</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-11</th>
      <td>2.242418</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.615912</td>
      <td>3.244750</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>5.533829</td>
      <td>4.250875</td>
      <td>NaN</td>
      <td>4.245998</td>
      <td>102.726746</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-12</th>
      <td>2.107934</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.615912</td>
      <td>3.329029</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>5.533829</td>
      <td>5.251082</td>
      <td>NaN</td>
      <td>3.912383</td>
      <td>101.704826</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-13</th>
      <td>2.339126</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.615912</td>
      <td>3.329029</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>5.970712</td>
      <td>5.001029</td>
      <td>NaN</td>
      <td>3.980611</td>
      <td>103.082207</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-14</th>
      <td>2.428280</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.621403</td>
      <td>3.202610</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>6.087214</td>
      <td>5.625959</td>
      <td>NaN</td>
      <td>4.306655</td>
      <td>104.481773</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>10 rows × 26 columns</p>
</div>




```python
close_final.head(10)
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
      <th>AAPL</th>
      <th>BETR</th>
      <th>BUFF</th>
      <th>CALM</th>
      <th>CENT</th>
      <th>CME</th>
      <th>DTEA</th>
      <th>FRPT</th>
      <th>GOOG</th>
      <th>KHC</th>
      <th>...</th>
      <th>PPC</th>
      <th>RELV</th>
      <th>RIBT</th>
      <th>SAFM</th>
      <th>SPY</th>
      <th>TOF</th>
      <th>VVI</th>
      <th>WILC</th>
      <th>WWAV</th>
      <th>agg</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2000-01-03</th>
      <td>9.207334</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>5.454494</td>
      <td>3.846159</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>8.021383</td>
      <td>-2.945864</td>
      <td>NaN</td>
      <td>6.060700</td>
      <td>4.069768</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-04</th>
      <td>-1.442326</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.000000</td>
      <td>0.645167</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>-1.058186</td>
      <td>6.249988</td>
      <td>NaN</td>
      <td>-8.333389</td>
      <td>-0.178554</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-05</th>
      <td>9.473724</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>-3.508792</td>
      <td>-0.641031</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>-5.499989</td>
      <td>0.000000</td>
      <td>NaN</td>
      <td>5.882369</td>
      <td>1.633390</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-06</th>
      <td>-4.522631</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>-2.439039</td>
      <td>3.231140</td>
      <td>NaN</td>
      <td>-2.857185</td>
      <td>-5.488844</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-07</th>
      <td>1.790248</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.000000</td>
      <td>2.631604</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>8.465613</td>
      <td>0.000000</td>
      <td>NaN</td>
      <td>2.941221</td>
      <td>-0.341915</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-10</th>
      <td>5.390877</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.785807</td>
      <td>-1.298713</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>-0.526290</td>
      <td>-8.828229</td>
      <td>NaN</td>
      <td>-2.857185</td>
      <td>1.211101</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-11</th>
      <td>6.379896</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.000000</td>
      <td>-2.531639</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>0.000000</td>
      <td>-19.047636</td>
      <td>NaN</td>
      <td>8.527156</td>
      <td>1.004790</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-12</th>
      <td>-9.883692</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>-7.317101</td>
      <td>5.000031</td>
      <td>NaN</td>
      <td>-1.714008</td>
      <td>-1.336197</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-13</th>
      <td>-3.671488</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>-0.883646</td>
      <td>3.947374</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>-1.913880</td>
      <td>-11.107973</td>
      <td>NaN</td>
      <td>-7.570702</td>
      <td>-1.339531</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-14</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>10 rows × 26 columns</p>
</div>




```python
covar = close_final.cov()

covar.head(10)
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
      <th>AAPL</th>
      <th>BETR</th>
      <th>BUFF</th>
      <th>CALM</th>
      <th>CENT</th>
      <th>CME</th>
      <th>DTEA</th>
      <th>FRPT</th>
      <th>GOOG</th>
      <th>KHC</th>
      <th>...</th>
      <th>PPC</th>
      <th>RELV</th>
      <th>RIBT</th>
      <th>SAFM</th>
      <th>SPY</th>
      <th>TOF</th>
      <th>VVI</th>
      <th>WILC</th>
      <th>WWAV</th>
      <th>agg</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>AAPL</th>
      <td>8.895495</td>
      <td>0.578006</td>
      <td>0.441937</td>
      <td>1.264006</td>
      <td>1.455844</td>
      <td>1.694867</td>
      <td>0.154084</td>
      <td>0.897254</td>
      <td>1.836266</td>
      <td>0.682035</td>
      <td>...</td>
      <td>1.098257</td>
      <td>0.050837</td>
      <td>0.508248</td>
      <td>1.075730</td>
      <td>1.623106</td>
      <td>NaN</td>
      <td>1.436867</td>
      <td>-4.072703</td>
      <td>NaN</td>
      <td>-0.059988</td>
    </tr>
    <tr>
      <th>BETR</th>
      <td>0.578006</td>
      <td>13.049084</td>
      <td>1.724265</td>
      <td>0.673226</td>
      <td>0.774846</td>
      <td>0.385839</td>
      <td>0.900242</td>
      <td>1.274864</td>
      <td>0.475736</td>
      <td>0.420337</td>
      <td>...</td>
      <td>0.827826</td>
      <td>1.496544</td>
      <td>-0.184863</td>
      <td>0.628844</td>
      <td>0.683926</td>
      <td>NaN</td>
      <td>0.496773</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.010206</td>
    </tr>
    <tr>
      <th>BUFF</th>
      <td>0.441937</td>
      <td>1.724265</td>
      <td>4.810366</td>
      <td>0.677561</td>
      <td>1.030790</td>
      <td>0.451542</td>
      <td>0.754770</td>
      <td>1.571576</td>
      <td>0.453654</td>
      <td>0.606145</td>
      <td>...</td>
      <td>0.775815</td>
      <td>-0.154047</td>
      <td>-0.066875</td>
      <td>0.730149</td>
      <td>0.571134</td>
      <td>NaN</td>
      <td>0.489106</td>
      <td>-1.036798</td>
      <td>NaN</td>
      <td>-0.012794</td>
    </tr>
    <tr>
      <th>CALM</th>
      <td>1.264006</td>
      <td>0.673226</td>
      <td>0.677561</td>
      <td>8.314661</td>
      <td>1.155322</td>
      <td>1.489070</td>
      <td>0.707045</td>
      <td>0.577692</td>
      <td>1.120575</td>
      <td>0.575955</td>
      <td>...</td>
      <td>1.965127</td>
      <td>0.454707</td>
      <td>1.178936</td>
      <td>1.308868</td>
      <td>0.951023</td>
      <td>NaN</td>
      <td>1.658525</td>
      <td>0.073846</td>
      <td>NaN</td>
      <td>-0.020696</td>
    </tr>
    <tr>
      <th>CENT</th>
      <td>1.455844</td>
      <td>0.774846</td>
      <td>1.030790</td>
      <td>1.155322</td>
      <td>9.922016</td>
      <td>1.747228</td>
      <td>0.451489</td>
      <td>1.034990</td>
      <td>1.403338</td>
      <td>0.785943</td>
      <td>...</td>
      <td>1.042613</td>
      <td>0.555477</td>
      <td>1.180167</td>
      <td>1.086711</td>
      <td>1.372155</td>
      <td>NaN</td>
      <td>2.336784</td>
      <td>-1.503545</td>
      <td>NaN</td>
      <td>-0.044425</td>
    </tr>
    <tr>
      <th>CME</th>
      <td>1.694867</td>
      <td>0.385839</td>
      <td>0.451542</td>
      <td>1.489070</td>
      <td>1.747228</td>
      <td>5.369265</td>
      <td>0.251257</td>
      <td>0.428709</td>
      <td>1.800073</td>
      <td>0.432083</td>
      <td>...</td>
      <td>2.034710</td>
      <td>0.561485</td>
      <td>1.010398</td>
      <td>1.436096</td>
      <td>1.596907</td>
      <td>NaN</td>
      <td>1.986680</td>
      <td>-0.768186</td>
      <td>NaN</td>
      <td>-0.125832</td>
    </tr>
    <tr>
      <th>DTEA</th>
      <td>0.154084</td>
      <td>0.900242</td>
      <td>0.754770</td>
      <td>0.707045</td>
      <td>0.451489</td>
      <td>0.251257</td>
      <td>22.477646</td>
      <td>0.846963</td>
      <td>0.130118</td>
      <td>0.471617</td>
      <td>...</td>
      <td>1.129738</td>
      <td>0.008399</td>
      <td>-0.534185</td>
      <td>0.627799</td>
      <td>0.356360</td>
      <td>NaN</td>
      <td>0.467363</td>
      <td>2.951310</td>
      <td>NaN</td>
      <td>0.018272</td>
    </tr>
    <tr>
      <th>FRPT</th>
      <td>0.897254</td>
      <td>1.274864</td>
      <td>1.571576</td>
      <td>0.577692</td>
      <td>1.034990</td>
      <td>0.428709</td>
      <td>0.846963</td>
      <td>10.491278</td>
      <td>0.490234</td>
      <td>0.897895</td>
      <td>...</td>
      <td>0.846426</td>
      <td>-0.225623</td>
      <td>0.576959</td>
      <td>0.597092</td>
      <td>0.642696</td>
      <td>NaN</td>
      <td>0.645580</td>
      <td>-2.743662</td>
      <td>NaN</td>
      <td>-0.037451</td>
    </tr>
    <tr>
      <th>GOOG</th>
      <td>1.836266</td>
      <td>0.475736</td>
      <td>0.453654</td>
      <td>1.120575</td>
      <td>1.403338</td>
      <td>1.800073</td>
      <td>0.130118</td>
      <td>0.490234</td>
      <td>3.621130</td>
      <td>0.754626</td>
      <td>...</td>
      <td>1.003766</td>
      <td>0.260870</td>
      <td>0.373841</td>
      <td>0.882783</td>
      <td>1.277741</td>
      <td>NaN</td>
      <td>1.370079</td>
      <td>-1.270653</td>
      <td>NaN</td>
      <td>-0.024299</td>
    </tr>
    <tr>
      <th>KHC</th>
      <td>0.682035</td>
      <td>0.420337</td>
      <td>0.606145</td>
      <td>0.575955</td>
      <td>0.785943</td>
      <td>0.432083</td>
      <td>0.471617</td>
      <td>0.897895</td>
      <td>0.754626</td>
      <td>1.638744</td>
      <td>...</td>
      <td>0.809656</td>
      <td>0.160541</td>
      <td>-0.301475</td>
      <td>0.658950</td>
      <td>0.591592</td>
      <td>NaN</td>
      <td>0.439923</td>
      <td>-1.357823</td>
      <td>NaN</td>
      <td>0.008824</td>
    </tr>
  </tbody>
</table>
<p>10 rows × 26 columns</p>
</div>




```python
market_temp = close_final.iloc[:,[20]]
market = market_temp.dropna()

```


```python
#total = sum(market)
mean_value = pd.DataFrame.mean(market)
print(mean_value)
variance = pd.DataFrame.var(market)
print(variance)
market.head(10)
```

    SPY   -0.011492
    dtype: float64
    SPY    1.480824
    dtype: float64





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
      <th>SPY</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2000-01-03</th>
      <td>4.069768</td>
    </tr>
    <tr>
      <th>2000-01-04</th>
      <td>-0.178554</td>
    </tr>
    <tr>
      <th>2000-01-05</th>
      <td>1.633390</td>
    </tr>
    <tr>
      <th>2000-01-06</th>
      <td>-5.488844</td>
    </tr>
    <tr>
      <th>2000-01-07</th>
      <td>-0.341915</td>
    </tr>
    <tr>
      <th>2000-01-10</th>
      <td>1.211101</td>
    </tr>
    <tr>
      <th>2000-01-11</th>
      <td>1.004790</td>
    </tr>
    <tr>
      <th>2000-01-12</th>
      <td>-1.336197</td>
    </tr>
    <tr>
      <th>2000-01-13</th>
      <td>-1.339531</td>
    </tr>
    <tr>
      <th>2000-01-18</th>
      <td>-0.807844</td>
    </tr>
  </tbody>
</table>
</div>




```python
covartotal = pd.DataFrame.sum(covar)
print(covartotal)
print(variance[[0][0]])

```

    AAPL    24.623828
    BETR    26.986567
    BUFF    16.812453
    CALM    28.138761
    CENT    31.026041
    CME     26.674849
    DTEA    34.010689
    FRPT    22.516264
    GOOG    20.357582
    KHC     12.087360
    LANC    15.664106
    LWAY    24.102763
    MSFT    20.212742
    NUTR     0.000000
    PF       5.824655
    POST    11.109943
    PPC     67.005785
    RELV    39.625424
    RIBT    49.511365
    SAFM    30.833337
    SPY     18.832532
    TOF      0.000000
    VVI     30.889375
    WILC    -4.233405
    WWAV     0.000000
    agg     -0.349838
    dtype: float64
    1.48082445212



```python
beta_appl = (covartotal/(variance[[0][0]] ** 2 ))

```


```python
beta_appl.head(100)
```




    AAPL    11.229190
    BETR    12.306668
    BUFF     7.666973
    CALM    12.832102
    CENT    14.148787
    CME     12.164516
    DTEA    15.509874
    FRPT    10.268078
    GOOG     9.283656
    KHC      5.512191
    LANC     7.143293
    LWAY    10.991569
    MSFT     9.217605
    NUTR     0.000000
    PF       2.656214
    POST     5.066461
    PPC     30.556608
    RELV    18.070359
    RIBT    22.578638
    SAFM    14.060908
    SPY      8.588188
    TOF      0.000000
    VVI     14.086463
    WILC    -1.930557
    WWAV     0.000000
    agg     -0.159537
    dtype: float64




```python
plt.plot(beta_appl)
```
![png](https://github.com/avnit/ContractWork/blob/master/output_14_1.png)
